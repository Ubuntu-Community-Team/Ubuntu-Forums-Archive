---
title: "Screensaver"
date: 2014-08-07
forum: General Help
---

### Post by UncleMonty on 2014-08-07
I'm using ubuntu 14.04 unity - I can't find the screensaver anywhere. :s Where exactly is it please?

---

### Post by grahammechanical on 2014-08-07
Ubuntu 14.04 does not have a screen saver and Ubuntu has not had one since Ubuntu 11.10 was released. This thread on the discourse.ubuntu site covers all the relevant points.

[http://discourse.ubuntu.com/t/ubuntu-14-04-screensaver/1637](http://discourse.ubuntu.com/t/ubuntu-14-04-screensaver/1637)

Regards.

---

### Post by Dennis N on 2014-08-07
Ubuntu 14.04 comes by default with gnome-screensaver, which provides a blank screen and no traditional screensavers. For those, you must install xscreensaver. 

Tips:
Disable or remove gnome-screensaver if you use xscreensaver.
The data packages providing the actual screensavers are separate:
xscreensaver-data (this one gets automatically installed with xscreensaver)
xscreensaver-data-extra
xscreensaver-gl
xscreensaver-gl-extra
rss-glx
Include xscreensaver in your startup applications. The command is **xscreensaver -no-splash**
rss-glx contains the more advanced and sophisticated screensavers. For instructions on getting these to work with xscreensaver, read:
[FONT=Courier New]**/usr/share/doc/rss-glx/README.xscreensaver**[/FONT]

---

