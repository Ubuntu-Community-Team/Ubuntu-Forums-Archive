---
title: "Can't log in."
date: 2007-12-21
forum: General Help
---

### Post by oehTie on 2007-12-21
Hello People,

As i am new to this forum, i hope i post in the right section. If not, feel free to let me know.

I have a problem with my ubuntu installation and it's getting kinda anoying. I managed to setup an Ubuntu instalation with webmin, apache webserver and MySQL. While trying to setup FTP access, i had to add my user account (which was the only one i have on this server) to the FTP group. Unfortunately i used a wrong command, adding me to the group but removing me from anything else.

When i use telnet, or a local console to log in, i get the standard welcome message:

> Ubuntu 7.10
testserver.tornadosolutions.nl login: theo
Password:
Last login: Fri Dec 21 09:56:07 CET 2007 from kmpn-c-afa7.mxs.adsl.euronet.nl
 pts/1
Linux testserver.tornadosolutions.nl 2.6.22-14-server #1 SMP Sun Oct 14 23:34
 GMT 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.



But instead of a command prompt, the following happens:
> 
Connection to host lost.

Press any key to continue...

Probably because the user account used is a member of the FTP group only.

Is there a way to fix this problem? I can give commands using webmin. But those are given as root, not as a user. Unfortunately, webmin can't do everything so i really need a good user account.

Thank you for any help.

oehTie The newby :)

---

### Post by oehTie on 2007-12-21
no-one?

---

