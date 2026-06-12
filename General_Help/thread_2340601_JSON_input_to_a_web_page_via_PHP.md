---
title: "JSON input to a web page via PHP"
date: 2016-10-20
forum: General Help
---

### Post by ELMIT on 2016-10-20
I got a program of which I only know that it sends a JSON event to a web site you specify. 
I could not get anything.

I wrote a simple php program:

```
<?php
header('Content-Type: application/json');

$myFile = "testFile.txt";
$fh = fopen($myFile, 'a') or die("can't open file");
$date = new DateTime();
$date = $date->format("Y-m-d H:i:s");
fwrite($fh, $date . "\n===================\n");

$error = '';

//Make sure that it is a POST request.
if(strcasecmp($_SERVER['REQUEST_METHOD'], 'POST') != 0){
    $error = "Request method must be POST!\n";
}

//Make sure that the content type of the POST request has been set to application/json
$contentType = isset($_SERVER["CONTENT_TYPE"]) ? trim($_SERVER["CONTENT_TYPE"]) : '';
if(strcasecmp($contentType, 'application/json') != 0){
    $error = $error . "Content type must be: application/json\n";
}

//Receive the RAW post data.
$content = trim(file_get_contents("php://input"));
 
//Attempt to decode the incoming RAW post data from JSON.
$decoded = json_decode($content, true);
 
//If json_decode failed, the JSON is invalid.
if(!is_array($decoded)){
    $error = $error . "Received content contained invalid JSON!\n";
}
 
//If error, put it into out put file
if($error) {
fwrite($fh, $error);
}

fwrite($fh, $decoded);
fclose($fh);

?>

```

The result is:
> 2016-10-20 16:39:14
===================
Content type must be: application/json
Received content contained invalid JSON!

As said, I have no influence on the sending part. Is there anything I can do on my receiving part?

---

### Post by dragonfly41 on 2016-10-20
Since the received content is reported to contain "invalid JSON" you can check that by pasting the JSON into here .. [http://www.jslint.com/](http://www.jslint.com/)

---

### Post by ELMIT on 2016-10-20
... and so we are at square 1.

I have no idea how to get the content of the JSON, therefore the program.

---

### Post by dragonfly41 on 2016-10-20
```

//Receive the RAW post data.
$content = trim(file_get_contents("php://input"));


//add this line to show the RAW data
alert($content);

```

---

