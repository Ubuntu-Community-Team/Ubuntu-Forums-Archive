---
title: "Tried to switch to proprietary nvidia driver: now x won't work. OH NOES, HALP."
date: 2007-12-29
forum: General Help
---

### Post by Chake99 on 2007-12-29
[http://xkcd.com/349/](http://xkcd.com/349/) It's so true.

Anyways, I started down the rabbit hole by changing my graphical options to be more jazzy: added shadows, translucency, the whole nine yards that I could find in the kubuntu appearance (or w/e it was truly called) tab. I rebooted to find X incredibly sluggish.

Enabling more hardware acceleration seemed like the best solution, so I went back to system settings, then the option with the monitor, then changed into administrator mode and went after the graphics card/acceleration settings.

Noting that I had downloaded the nvidia drivers (or so I believed). I checked the proprietary box, scrolled down and selected nvidia and geforce 4 (generic).

Upon trying to reboot I came to the realization x wouldn't start and I was instead stuck on the CLI. Typing startx did not change this, but instead filled up the screen with messages that I did not understand but from which I surmised something was very wrong. 

How can I get my linux partition to revert to nv / get x to work again?

Thanks in advance. (EDIT: using Gutsy Gibbon 7.10 Kubuntu)

---

### Post by taurus on 2007-12-29
```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by freymann on 2007-12-29
> **Chake99 said:**
> 
Anyways, I started down the rabbit hole by changing my graphical options to be more jazzy: added shadows, translucency, the whole nine yards that I could find in the kubuntu appearance (or w/e it was truly called) tab. I rebooted to find X incredibly sluggish.

Upon trying to reboot I came to the realization x wouldn't start and I was instead stuck on the CLI. Typing startx did not change this, but instead filled up the screen with messages that I did not understand but from which I surmised something was very wrong. 

How can I get my linux partition to revert to nv / get x to work again?



 Awh the things we wished we had done before we had gone and broke things.... 

 Look in /etc/X11/

 You'll probably find a few backup files of xorg.conf.

 Copy some of the backups over to xorg.conf and see what happens.

 And when you do get things working, copy a working version of /etc/X11/xorg.conf to your home directory to rescue you later!

---

### Post by Chake99 on 2007-12-29
the first suggestion worked. Excellent. I actually found the same suggestion in a forum search but the person had left a space after the dpkg and before the dash so the command was invalid.

---

