[![Build Status](https://travis-ci.org/wrannaman/base64image.svg)](https://travis-ci.org/wrannaman/base64image)  

base64image
=================

Download images from remote URLs or use local images and encode/decode them to base64

To install  
`npm install base64image --save`  

To run tests  
`npm test`  

### Usage  

Require the library in your .js file  
`var base64 = require('base64image');`  

#### Download and encode an image  
```
var options = {string: true};

base64.base64encoder('www.someurl.com/image.jpg', options, function (err, image) {
    if (err) {
        console.log(err);
    }
    console.log(image);
});
```

#### Encode a local image  
```  
var path = __dirname + '/../test.jpg',
          options = {localFile: true, string: true};

base64.base64encoder(path, options, function (err, image) {  
    if (err) { console.log(err); }  
    console.log(image);  
});  
```


##### Parameters  
 - `url` (string) - the url of the image to be downloaded and encoded.
 - `options` (object)
 	- if `string` is passed is with 'true', the image returned will be a base64 string. Otherwise, the base64 buffer is returned.  
 	- if `localFile` is passed is with 'true', a local image instead of a remote one will be used  
 - `callback` (function) - the callback will contain the err object and the encoded image object.  

#### Decode and write a base64 encoded image to disk  
```  
var options = {filename: 'test', filePath: './tmp/uploads'};
var imageData = new Buffer('/9j/4AAQSkZJRgABAQAAAQABAAD...', 'base64');

base64.base64decoder(imageData, options, function (err, saved) {
    if (err) { console.log(err); }  
    console.log(saved);    
});  
```  

##### Parameters  
 - `imageData` (buffer) - the base64 image buffer.  
 - `options` (object) - contains the 'filename' property; this will be the written image file.  Also, you can specify a filePath which takes a directory path to write the file to. The directory path must exist already ( @TODO ).
 - `callback` (function) - the callback will contain the err object and the 'successful save' string.

### License  
This library is licensed under the MIT license.  

### Issues  
Report a bug in the issues.   

Updated by Wrannaman & forked From [Riyadh Al Nur](http://blog.verticalaxisbd.com)
