---
title: "Hiding ALL pre-login &amp; reboot terminal text"
date: 2014-05-16
forum: General Help
---

### Post by tom92 on 2014-05-16
Hi,

I've been trying to hide the terminal messages that come (a) right after the plymouth splash and (b) right after a reboot/shutdown:
[http://i.imgur.com/pqNFuT0.png](http://i.imgur.com/pqNFuT0.png)
[http://i.imgur.com/mIGZo14.png](http://i.imgur.com/mIGZo14.png)


I tried:
Disabling tty1-6 terminals (by renaming tty* .conf files in /etc/init) gets rid of "xbmc login:" text.
Disabling the greeting (by sudo nano /etc/issue) gets rid of the Ubuntu banner.
But you still have a blinking cursor and some flashing text.


I also tried:
putting "setterm -term linux -foreground black" on the /etc/init.d/ scripts, but no luck


Any ideas how to get hide or change the color of terminal text in Ubuntu 13.04 on boot / reboot ?

---

### Post by grahammechanical on 2014-05-16
What you are seeing is Linux loading and putting out its messages. Without Linux loading we do not get Ubuntu or any other Linux distribution loading. There is a Linux boot parameter called: quite but despite that being default we still get some messages. 

Read this to see that you are not asking for an easy answer. Certainly it is not an answer that I know of.

[http://www.refining-linux.org/archives/4/Boot-your-Linux-silently/](http://www.refining-linux.org/archives/4/Boot-your-Linux-silently/)

Regards.

---

