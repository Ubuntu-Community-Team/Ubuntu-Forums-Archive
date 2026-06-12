---
title: "Avast4Server"
date: 2008-04-13
forum: General Help
---

### Post by Trekster on 2008-04-13
Hi Guys,

I'm trying to install avast4server on my Ubuntu 7.04 server. I *think* i tried to install it before and it got broken somehow and now everytime i try to install it i get this:

sudo dpkg -i avast4server-3.0.1-i586.deb

Selecting previously deselected package avast4server.
(Reading database ... 116781 files and directories currently installed.)
Unpacking avast4server (from avast4server-3.0.1-i586.deb) ...
.: 93: Can't open /etc/sysconfig/avastd
invoke-rc.d: initscript avastd, action "stop" failed.
dpkg: error processing avast4server-3.0.1-i586.deb (--install):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 avast4server-3.0.1-i586.deb


I have tried everything i know to clean the avast installation up but had no luck with it.

Any suggestions?

---

