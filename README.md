# flickrUpload.js

This javascript module is for uploading the picture to Flickr with OAuth.
http://www.flickr.com/services/api/upload.api.html is the API doc but this doesn't describe how to do with OAuth autentication.
Implemented OAuth authentication with digesting several Flickr Discussion pages.

* http://www.flickr.com/groups/api/discuss/72157626950280601/
* http://www.flickr.com/services/api/upload.example.html
* http://www.flickr.com/groups/api/discuss/72157631693117187/

## Browsers

It has been tested on the following browsers

* Firefox 19.0.2
* Google Chrome 25.0.1364.172
* Safari 6.0.3 

## How to use

### Load this module 

    <script type="text/javascript" src="flickrUpload.js"></script>

### Prepare OAuth and parameters

This module DOES NOT cover the creation of oauth keys and parameters. Please prepare the parameters beforehand. 
The parameters would be like below.

    var params = {
        description: "desc1",
        oauth_consumer_key : "xxxxx_your_consumer_key_xxxxx",
        oauth_nonce : "77e66489c35f97cc54a3ca20a88149f1efe906da",
        oauth_signature : "quWKoqMsaxCRKRB7yAVc8gSv0yU=",
        oauth_signature_method : "HMAC-SHA1",
        oauth_timestamp : "1364002382",
        oauth_token: "xxxx_your_oauth_token_xxxxx",
        oauth_version: "1.0",
        tags: "tags1",
        title: "title1"
    };

These oauth keys should be calculated on server end intead of client(browser) for security concern.
These parameters can be obtained using API kits under http://www.flickr.com/services/api/.

*If you want to implement OAuth keys, you may be able to use http://oauth.googlecode.com/svn/code/javascript/* 

## Example

    photoid = flickrUpload.post(params, 'http://api.flickr.com/services/upload', binary);

* Retrun photoid. "error" if failed the query
* params is the parameters (oauth keys + parameter(title, description,,,))
* binary is the binary of the photo you want to upload 


You can take a look at example.html for details. What the example does is as following: 

1. Put image to canvas 
2. Convert canvas to binary 
3. Obtain paramters from server 
4. Post with flickrUpload

## Trouble? 

### invalid signature?  

Manually put the entry in the below and make sure that the OAuth signature is correct.

 * http://oauth.googlecode.com/svn/code/javascript/example/signature.html

