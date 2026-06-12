---
title: "Is flashplayer on Ubuntu possible?"
date: 2013-09-21
forum: General Help
---

### Post by ian19 on 2013-09-21
Flash player is availabe on modern phones easily enough. 2 hours with ubuntu and nothing. 
   windows nt is nearly better than this os at this stage.
    Why is it so difficult to get flash on ubuntu.
      Here's what ive done so far to get it working ,
         tried a flash player update, the restricted package,the flash package from ubuntu software center and installing through firefox and chromium.
  

Did you install flash on your ubuntu and how did you get it working?

---

### Post by XBNCPRk on 2013-09-21
Have never had any issue with it with either chrome or chromium... plays everything, updates itself, etcetc. 

Ubuntu version? Hardware specs?

---

### Post by QIII on 2013-09-21
I'm using it on several machines with Firefox.

Flash has always been problematic in Linux -- not because of Linux, but because Flash has never supported Linux well.  

It has always worked in Windows because its developers have always made sure it did.  Microsoft doesn't support Flash.  It's important to understand that relationship.

I installed Flash via the command line from the repositories.

---

### Post by ibjsb4 on 2013-09-22
I did not realize it was still in the repositories.  I was under the impression it was dropped after 12.04.

---

### Post by QIII on 2013-09-22
13.04, installer is still there:

[ATTACH=CONFIG]246421[/ATTACH]

---

### Post by ibjsb4 on 2013-09-22
Yep
[https://apps.ubuntu.com/cat/applications/raring/adobe-flashplugin/](https://apps.ubuntu.com/cat/applications/raring/adobe-flashplugin/)

I guess its no longer part of the restricted-extra though.

---

### Post by kurt18947 on 2013-09-22
Flash is available via the repositories in 13.10.  There are two restricted packages, I'm not sure which one contains the flash installer.  Touch wood, I've never had an issue installing flash or playing content.

---

### Post by debodas on 2013-09-22
Alternatively, Google Chrome comes with flash.

---

### Post by claracc on 2013-09-22
Have you tried to install through any of these two methods?:

[http://linuxg.net/how-to-install-adobe-flash-player-in-ubuntu-13-04-ubuntu-12-10-and-12-04/](http://linuxg.net/how-to-install-adobe-flash-player-in-ubuntu-13-04-ubuntu-12-10-and-12-04/)

---

### Post by vasa1 on 2013-09-22
Beginning to look like a drive-by ...

---

### Post by ian19 on 2013-09-22
have ubuntu 12.04 with wubi. its installed on the hard drive. In the software center on the launcher there was a flash installer but it failed to install.

---

### Post by ian19 on 2013-09-22
I live in Ireland.  Posted this around 3 am last night. people need sleep.

---

### Post by ian19 on 2013-09-22
thats exactly what I thought but don't have you to install it through the web store.

---

### Post by ian19 on 2013-09-22
Have ubuntu version 12.04 installed on a hard drive thanks to wubi. My pc is a dell d630 with 2 gb of ram with a dual core 1.8ghz

---

### Post by ian19 on 2013-09-22
SOLUTION,
Not 100 per cent sure how I managed to do this but it was a combination of these methods, 
[http://linuxg.net/how-to-install-adobe-flash-player-in-ubuntu-13-04-ubuntu-12-10-and-12-04/](http://linuxg.net/how-to-install-adobe-flash-player-in-ubuntu-13-04-ubuntu-12-10-and-12-04/)

The trick is to restart your browsers.

Haven't tried this method yet, could be helpful for those looking to install flash too.
If the flash in the ubuntu software center doesnt work, you can try this

> For any one having trouble with installing, use your terminal. I didn't even need to restart FF.Open Terminal
cut & paste  ------->                             sudo apt-get install flashplugin-installer gsfonts-x11


hit enter, type your pwd,hit enter, download starts, type Y when asks for install & a few seconds later you can watch YT etc. 


Hope it helps you a bit  :)


bt

---

