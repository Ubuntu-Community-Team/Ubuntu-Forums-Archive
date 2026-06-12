---
title: "Xserver Crash"
date: 2007-03-24
forum: General Help
---

### Post by golf22r on 2007-03-24
I tried to install Nvidia drivers by running: sudo aptitude install nvidia-glx nvidia-kernel-common   and then sudo nvidia-xconfig   This resulted in an Xserver crash.  I booted into recovery mode and ran dpkg-reconfigure –phigh xerver-xorg  and then startx  it returned 
  Fatal server error:
  No screens found
  XIO:    fatal IO error 104 (Connection reset by peer) on X server “:0.0”
              After 0 requests (0 known processed) with 0 events remaining 
   
  Does anybody know how to fix this problem?  Thank you!

---

### Post by smokey edgy on 2007-03-24
Hi golf22r,

I ran into somewhat similar issues installing my ATI x1950. Is this a fresh install from the CD? If so, you might need to rerun 'dpkg-reconfigure –phigh xerver-xorg' and use vesa (instead of nvidia) temporarily. Try doing startx again, and if it still gives you a fatal screen error check in your /etc/X11/xorg.conf file. There should be a section that looks something like this:

Section "Device"
        Identifier  "Generic Video Card"
        Driver      "vesa"
        BusID       "PCI:3:0:0"
EndSection

If you see a BusID there, remove it and try restarting X again. Hopefully it will start up. If it does, make sure you run all the updates that need to be run. Then try following one of the great step-by-step docs on how to install the nvidia drivers (which I'm guessing you did before).

smokey edgy

---

### Post by golf22r on 2007-03-24
It is not a fresh install.  The problems originated when I attempted to upgrade my kernel.  I switched to the Vesa driver, and I can get to my desktop.  From there I tried to install the Nvidia driver using Automatix2 which said it had an apt-get error.  Then I tied install the drivers with Envy, a GUI for graphics card installations.  It said it was successful, but when I restarted i was back to the xserver crash.

---

### Post by smokey edgy on 2007-03-24
You may want to double check the logs for both Automatix2 and envy. I seem to recall envy continuing on with its scripts even though there were issues with getting packages. It may be worth figuring out why does apt-get errors occurred and fixing them.

They were working with your previous version of the kernel? You may want to look at compiling the drivers from scratch (which I think envy may or may not do). 

Try taking a look at the xorg logs in /var/log/Xorg.0.log.

Hope this leads you somewhere.

---

