---
title: "[lubuntu] Ubuntu ignores my power settings and &quot;This session is locked&quot;"
date: 2014-07-06
forum: General Help
---

### Post by JimmyRcom on 2014-07-06
I've been keeping up to date weekly with lubuntu. With the latest update ubuntu ignores my power settings. It suspends when I close the lid now. I followed this guide and now it works again, it does not suspend when closing the lid.
[http://askubuntu.com/questions/363795/closing-laptop-lid-suspends-lubuntu-since-upgrade](http://askubuntu.com/questions/363795/closing-laptop-lid-suspends-lubuntu-since-upgrade)

But now it automatically locks the screen if I'm idle after a certain time. Not only that it turns off the backlight. It does that on startup too, I put a command in lxde autostart to fix it. I have to go into another computer and use 
xbacklight -set 10 -d ":0"

I can see the screen when I switch back. But then I see "this session is locked you will be redirected automatically in a few seconds", then it redirects to the login screen but blacks out my screen again to where I can barely see the login box. I can't get the backlight to turn on from here even from the other machine without switching to console then switching back to tty 7 and having it show me the "session locked redirect" thing again. 

```
 % lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

```

Installing ubuntu this go around was kinda tricky. I also had these issues
Screen backlight is 0 on startup.
[http://askubuntu.com/questions/329059/no-partitions-showing-during-installation](http://askubuntu.com/questions/329059/no-partitions-showing-during-installation)
Normal partitioning from latest ubuntu usb didn't work. Had to destroy partitions with gparted in live usb mode. Installer could never detect partitions.

---

