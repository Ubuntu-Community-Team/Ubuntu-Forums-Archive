---
title: "No login Screen with nvidia drivers installed /dual montitor broke without nvidia"
date: 2015-04-27
forum: General Help
---

### Post by jarrod4 on 2015-04-27
I know there are a million threads about nvidia drivers.  I've looked through countless threads.  My issue is that I had a working system, I patched the system and broke it.  I have tried to back out all the changes to get back to a working system with no luck.

The system is a Dell M6400 with a 14.04LTS
Nvidia 3700M card
Dell Docking station with 2 24" monitors

If I install Nvida drivers I get a blank login page
If remove the laptop from the docking station I can log in
If I purge the nvidia driver I can be docked, and I can log in, but I only get one monitor, and the control panel will not recognize the other monitor


I have purged nvdia
I have purged xserver
I have purged lightdm
I have renamed the existing x directories in /etc/x11 and /bin/x and forced a re-install
I have rm ~/.config/monitors.xml

I have reinstalled all those packages listed above.  Same behavior.  While docked, I only get one monitor.  I have confirmed the monitor is connected and working. 

xrandr does not show the second monitor.

If I install the nvidia specific drivers, or the nvidia-current from the xorg ppa the system breaks (no login screen).  I have also tried the nvidia driver from the nvidia website (340.76) with the same result.

Muck of the online documentation talks about looking at /etc/x11/xorg.conf  I don't have an xorg.conf file.  Is there another config somewhere else i need to remove/edit?

---

### Post by jarrod4 on 2015-04-28
Anyone?

---

