---
title: "Problem booting into graphical mode with Edgy"
date: 2006-10-27
forum: General Help
---

### Post by f0rk on 2006-10-27
Yesterday evening I updated my Kubuntu system from Dapper to Edgy. I checked it out this morning, and the system was working properly.

Here's what happened. In KDE I went into the system settings, and selected the 'hardware' option, and when It loaded I clicked 'configure', and picked out a proprietary nvidia driver to use with my graphics card, which is an nvidia card (of course). I got the "This configuration cannot be safely tested" message after I applied the changes. Then I re-booted. The system stalled duringthe re-boot, so I did a cold boot, and the system booted fine, but instead of getting the friendly login screen after boot up the screen stayed black. I hit F1 and got a login prompt on the command line, and I logged in. After logging in I tried 'startx' and got the usual "X server already running" message ... I edited my xorg.conf file to set it up the way it was before I changed the video driver, and re-booted. NO problem on the re-boot, but I still got a black screen. I switched the default runlevel to 5 by editing the /set/inittab file and re-botted again, with the same problem. Startx does eventually work, and XFCE (my alternate desktop environment) loads up fine, but I cant get the system to boot up into the graphical mode anymore.

Can anybody please help? Thank you for your time.

---

