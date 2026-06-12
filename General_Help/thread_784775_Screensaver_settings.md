---
title: "Screensaver settings"
date: 2008-05-06
forum: General Help
---

### Post by apokkalyps on 2008-05-06
Does the Compiz screensaver override the default gnome screensaver?  I cant figure out the relationship between the two.  Do I have to turn one off to use the other?  

What I'd like to do is use the spinning cube as my screensaver, but then after so much time, have the gnome screensaver take over and/or power off my monitor.

---

### Post by 01000111 on 2008-05-13
> **apokkalyps said:**
> Does the Compiz screensaver override the default gnome screensaver?  I cant figure out the relationship between the two.  Do I have to turn one off to use the other?  

What I'd like to do is use the spinning cube as my screensaver, but then after so much time, have the gnome screensaver take over and/or power off my monitor.


The easy way to do this is to set the Compiz screensaver the way you want, then set the DPMS timeout to when you want the monitors to go into standby using:  xset dpms 600  (that will put them in standby in 10 minutes).

In order for DPMS to work, it must be set in your xorg.conf, so make sure the monitor section of your xorg.conf has the line:
    Option         "DPMS"


01000111

--------
There are 10 types of people in the world. Those who understand binary, and those who don't.

---

