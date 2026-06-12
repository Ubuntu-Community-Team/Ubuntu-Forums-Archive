---
title: "xubuntu: light-locker not working (desktop) (14.04)"
date: 2014-06-21
forum: General Help
---

### Post by anewbie on 2014-06-21
I have a clean install of xubuntu 14.04 (well I installed ubuntu desktop and then apt-get xubuntu-desktop). My home directory is very very old (maybe there is some old cruff in there impacting my usage). I have two bugs:


light-locker will not work. I.e, I have time set to 5 minutes to lock/blank screen and neither happens. If I manually lock the screen it immediately locks and then a minute later goes into power saving mode (for the monitor) which is what I want.
-
xscreensaver is not installed (read release notes).
-
The second bug is if I turn the monitor off and then the monitor goes into power saving mode (system I mean); the monitor will not wake up (exit power saving mode) if I move the mouse or keyboard (it correctly wakes up if i lock the screen manually and let it go into power saving mode). I'm using intel hd2500 (sandy bridge I5) this is a desktop and the system itself is not entering suspend/hibernation mode (which is correct). 
-
I did a bit of googling and can't seem to find references to the first bug; the second bug might be related to the problem some folks have with laptop but not sure. Any suggestions for why light-locker doesn't work or how to fix these two issues (other than switching back to ubuntu).
-
While this is a clean 14.04 install I was running 12.04 without these issues (the upgrade failed megatime so I had to do a clean install).
-

---

### Post by Dennis N on 2014-06-21
> I installed ubuntu desktop and then apt-get xubuntu-desktop
Based on this information, you could have gnome-screensaver installed with ubuntu-desktop, along with light-locker from xubuntu-desktop. Try removing (or disabling) gnome-screensaver.

---

### Post by anewbie on 2014-06-21
That helps a little but not completely. I did not reboot the system or restart lightdm; but i did uninstall gnome-screensaver and killed all running instances. If I kill tvtime it will lock now; but if tvtime is iconfied but running it sitll does not blank screen/lock. I should have mentioned tvtime before in case it is relevant but under ubuntu 12.04 iconifiying tvtime was enough to start the timer....

---

