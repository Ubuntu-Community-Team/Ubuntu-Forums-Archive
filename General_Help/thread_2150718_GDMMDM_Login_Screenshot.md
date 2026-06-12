---
title: "GDM/MDM Login Screenshot"
date: 2013-06-02
forum: General Help
---

### Post by CosmicFlux on 2013-06-02
Hi,

I'm running Lubuntu 13.04 and using MDM as my login manager. I'm trying to take a screenshot of my login screen and every method I know of has turned up error messages. 

I've tried:

**adding **(gnome-screenshot -d 5) &** to the*/etc/mdm/Init/Default *config file. 
**export DISPLAY=:0.0 ; sudo -u mdm gnome-screenshot
**chvt 7; sleep 5; XAUTHORITY=/var/mdm/:0.Xauth DISPLAY=:0.0 import -window root /tmp/mdm-login-shot.png

All of the above are throwing out error messages, such as no protocol found - cannot open X Display etc.

The first option seems to work - the screen flashes after 5 seconds - but the output file is absolutely nowhere to be found. 

I'm at a loss!


Cosmic

---

### Post by MG&amp;TL on 2013-06-02
I think you might want to look into [http://www.dedoimedo.com/computers/xephyr.html](http://www.dedoimedo.com/computers/xephyr.html) (Xephyr), but I'm not sure how to get it working with, say, GDM.

---

### Post by CosmicFlux on 2013-06-04
OK thanks for your help. Got what I wanted!


Cosmic

---

