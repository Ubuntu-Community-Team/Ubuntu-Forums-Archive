---
title: "Broken package error - cannot fix"
date: 2016-06-23
forum: General Help
---

### Post by jub2 on 2016-06-23
In a live session (with persistence) of Xubuntu 14.04.4 LTS, I tried to install fglrx (AMD proprietary graphics driver) and received broken package errors in both Synaptic and terminal. Output from terminal:

[[IMG]http://i175.photobucket.com/albums/w128/pbucket_pics/misc/terminal.png[/IMG]]("http://s175.photobucket.com/user/pbucket_pics/media/misc/terminal.png.html")


Ran "Fix Broken Packages" in Synaptic, and received the following message:

[[IMG]http://i175.photobucket.com/albums/w128/pbucket_pics/misc/synaptic.png[/IMG]]("http://s175.photobucket.com/user/pbucket_pics/media/misc/synaptic.png.html")

Any suggestions on how to proceed?

---

### Post by ajgreeny on 2016-06-23
It is a long time since I used a live system for anything but installing an OS, but I am pretty sure that you can not install an xorg driver, eg fglrx, in a live system, even with persistence, as the driver is part of the OS itself, so when you reboot it will be gone.

Only files that you create and save as the live user will be saved for you and remain in their appropriate live system home after rebooting.

---

