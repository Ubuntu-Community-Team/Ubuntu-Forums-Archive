---
title: "how to encode URL?"
date: 2005-06-04
forum: General Help
---

### Post by nemik on 2005-06-04
Hello,

First just want to say how much i love ubuntu! excellent OS and so easy to use, it is my first linux distro!

now my problem/question. i installed SMStools and they work great. i'm now making my own eventhandler for incoming SMS where i want to pass the phone number it came from and the text in the SMS to a PHP script via variables in the URL. i do this with cURL. (ex: http://www.mydomain.com/my.php?from=$FROM&$message=$TEXT)

so far so good except for when the text has wierd characters or line breaks, cURL does not like it and spits an error. it is because it is not URL encoded for it to be passed. so now i'm wondering, how can I go about URL-encoding the $TEXT string so i can properly pass it to the remote PHP script?

any help would be REALLY appreciated!

Thank you everyone!

---

### Post by Moobert on 2005-06-04
theres

[http://uk2.php.net/manual/en/function.base64-encode.php](http://uk2.php.net/manual/en/function.base64-encode.php)

and to decode:

[http://uk2.php.net/manual/en/function.base64-decode.php](http://uk2.php.net/manual/en/function.base64-decode.php)

Sending via the url seems inefficient, can't you setup a html form and then post the data to the php ?

or save to a format like say xml and then get the php script to read it ?

---

### Post by nemik on 2005-06-04
[QUOTE=Moobert]theres

[http://uk2.php.net/manual/en/function.base64-encode.php](http://uk2.php.net/manual/en/function.base64-encode.php)

and to decode:

[http://uk2.php.net/manual/en/function.base64-decode.php](http://uk2.php.net/manual/en/function.base64-decode.php)

Sending via the url seems inefficient, can't you setup a html form and then post the data to the php ?

or save to a format like say xml and then get the php script to read it ?[/QUOTE]


well i have a program that sends AT serial commands to my phone every few seconds and picked up recieved SMS text messages from it and saves them to a file.
the program also has a feature to allow an eventhandler (which has to be a shell bash script) to do something with the recieved message.
i can extract the phone number no problem and send it as a variable to my PHP script, but the text itself that the user sent has spaces and other characters that need to be URL encoded in order for them to be passed into the PHP by cURL.

the functions you gave me i use in PHP already and they're great, but i need something that will encode URLs in the shell bash script.

i found this: [http://www.shelldorado.com/scripts/cmds/urlencode.txt](http://www.shelldorado.com/scripts/cmds/urlencode.txt) but have no idea how to implement it to make it work.

---

### Post by nemik on 2005-06-04
ok i got it working!!! i used the url_encode function from here: [http://djini.de/software/shell/leo](http://djini.de/software/shell/leo) in case anyone else has a similar problem.

---

