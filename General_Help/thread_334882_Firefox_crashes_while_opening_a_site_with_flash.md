---
title: "Firefox crashes while opening a site with flash"
date: 2007-01-09
forum: General Help
---

### Post by sankarnkp on 2007-01-09
Friends,
I am running Ubuntu 6.10 with Firefox 2. I installed flash player plugins and after that when I open any site with flash then firefox crashes. I have no idea why this happens because in my FC5 I have done same things to install flash plug in and have no problem there. Right now I have deleted the flash plugins and keeping firefox run. I need some help so that I can open youtube again!!! :D

---

### Post by useResa on 2007-01-09
This item is discussed [here](http://www.ubuntuforums.org/showthread.php?t=286069&highlight=edgy+firefox+flash+crash).

Hope this will help you YouTube-ing again  :D

---

### Post by infol on 2007-01-09
hi sankamkp

what version of flash (or gnash) did you install - and how did you install it? the easiest solution would probably be to remove your current version by 
```
sudo apt-get remove flashplugin-nonfree mozilla-plugin-gnash gnash
```
or whatever you might have installed..

(if compiled from source) 
```
sudo dpkg -r *package name*
```

and then reinstall; the latest beta you can find here: 
[http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

(alternatively, you can install automatix or something similar to install it for you)

---

### Post by justinflavin on 2007-01-11
installing flash 9 beta worked for me - and i've tried every other solution.  i'm no longer getting firefox crashes on youtube. (firefox 1.5.0.7, dapper drake)

---

