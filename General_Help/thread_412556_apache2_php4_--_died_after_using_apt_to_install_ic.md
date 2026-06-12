---
title: "apache2 php4 -- died after using apt to install icecast2"
date: 2007-04-18
forum: General Help
---

### Post by inspiteofmyself on 2007-04-18
im not a complete noob...but really prefer using packages to custom building apps like apache/php. i installed apache2 and php4 yesterday. then installed a script called phpmp (php application to control mpd). all was well, then i decided that i wanted to stream to my lan (via icecast2) for use on devices like my PSP, my workstation, etc...so i apt-get icecast2...it immediately installs apache as a dependency, seems to all be ok...but icecast2 never really does get itself to a point that it wants to work.

best i can tell, the icecast2 package was compiled to use crypt for passwords, and mpd does not support crypt (no idea, im going by what i read on other sites)

anyway, i remove icecast, i remove apache, and suddenly nothing is working. ive removed (completely) apache2, and php4 as well as reinstalling them...and for some reason php docs download in firefox.

if i use lynx to examine the headers returned by the server, i see the following:

```
HTTP/1.1 200 OK
Date: Wed, 18 Apr 2007 12:09:48 GMT
Server: Apache/2.0.55 (Ubuntu)
Last-Modified: Wed, 18 Apr 2007 11:56:13 GMT
ETag: "1c428c-13-c5dad140"
Accept-Ranges: bytes
Content-Length: 19
Connection: close
Content-Type: application/x-httpd-php

```

that mimetype is set in apache2.conf, and in mime.types 

ive tried using a2enmod to enable the apache module, but when i run it i get the following:

```

root@fluid-laptop:/etc# sudo a2enmod php4
This module does not exist!

```

however, libapache2-mod-php4 is indeed installed...

help???

---

