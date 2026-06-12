---
title: "Firefox &amp; Hyphens."
date: 2004-12-17
forum: General Help
---

### Post by sgnlfive on 2004-12-17
I searched but couldn't find anything so forgive me if this is a repeat topic.

Anywho - The error is mainly with URLs with hyphens in them, I can't seem to connect to any sites that have hyphens in them on DeviantART.

Example: [http://books-.deviantart.com](http://books-.deviantart.com)

There was a fix for this posted on DevART, but they don't allow searching through the forums, and I can't remember how it was done. Any help would be great. Thanks.

---

### Post by wulf on 2004-12-17
Hyphens? I've not had any problems (just as well, as my personal domain is web-den.org.uk). The one you quote looks odd though - I can't remember seeing a specified server name ending in a hyphen! FWIW, I can't reach that site either.

Wulf

---

### Post by sgnlfive on 2004-12-17
Yeah it is just on devintart art.

what they do is when a new user signs up it makes there user name in the url.

example:

username.deniantart.com

and they allow hyphens at the last cjaracter, even the first.

---

### Post by wulf on 2004-12-17
[QUOTE=sgnlfive]Yeah it is just on devintart art.

what they do is when a new user signs up it makes there user name in the url.

example:

username.deniantart.com

and they allow hyphens at the last cjaracter, even the first.[/QUOTE]
 Maybe it's something they do deliberately to protect certain areas from access by unregistered users? I haven't come across it before though.

Wulf

---

### Post by sgnlfive on 2004-12-17
nah its just people who couldnt come up with a unique username :)

there are quite a few people who have hyphens

for the record this is only a problem under linux.

---

### Post by sgnlfive on 2004-12-17
woo! I have figured it out.

Just add this line to the /etc/hosts

69.28.181.43 books-.deviantart.com

then reboot.  ;-)

where "books-" is just make a new line with another users name if they have a hyphen @ the end of their username.

---

