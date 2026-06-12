---
title: "Apache 2 help (Debian)"
date: 2007-07-20
forum: General Help
---

### Post by Big_Croc7 on 2007-07-20
Hi, can anyone point me to an absolute starters' guide for setting up apache 2?  I've tried goolgle ;-) but all I can find seems to be things geared at people who already know how the whole thing works... I just want to set up a very basic server with some static web pages.  I've got the install from the repos done ok - at least, if I go to 127.0.0.1 with a browser I get a page saying 'it worked', but where do I put my content??

I've tried adding lines specifying documentroot=/home/web to httpd.conf and apache2.conf, then restarting the service, but nothing seems to work; I still just get a page saying 'it worked'.  All the config info seems to be in apache2.conf instead of httpd.conf as well.

NB. This is actually under a Debian install (on a dual-boot), but I was hoping you guys could help me out since I'm more familiar with these forums ;-)  I assume it's the same in Ubuntu/Debian anyway.

---

### Post by anubhavrocks on 2007-07-20
put your html page in 
/var/www

also be sure that the permissions are in place

---

### Post by matthew on 2007-07-20
/var/www

EDIT: someone beat me to it! :)

---

### Post by Big_Croc7 on 2007-07-20
Thanks very much for the prompt reply! Cheers!

---

