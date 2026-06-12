---
title: "Computer would not load desktop [SOLVED]"
date: 2015-02-18
forum: General Help
---

### Post by valvegrid on 2015-02-18
I am speaking in past tense because although I've cured the problem I'm wondering if anyone else has had the same issue.

This morning I accepted some software upgrades, this evening I switched on the computer and signed in only to find the computer would not load the desktop, I tried everything including searching this site, but nothing. It was booting OK, so it was getting past grub, but it was just getting to where the desktop should load and it was just sitting there doing nothing with 14.04 in the bottom left corner with the wallpaper.

I had some suspicion it might be a graphics problem, I am using an Nvidia card and downloading the drivers from the Nvidia site, I've been doing that for years without a problem at all. I decided to try reinstalling them and presto, the desktop came back to life.

Does anyone know what the latest upgrades where? I might give some clue as to why it happened, so I'll be able to recognise the problem if it reoccurs.  

Hopefully it might help someone else who might encounter the same problem.

Thanks in anticipation.

---

### Post by valvegrid on 2015-02-18
Further to my possible problem, I've just had a look at the last update and I notice there was one entry 'xserver-xorg-video-all' I'm wondering if this could be the culprit as it's related to the graphics? But just looking down the list there are others that could have busted the graphics, so I'm not sure.

```
Commit Log for Mon Feb 16 21:48:43 2015



Upgraded the following packages:
apport (2.14.1-0ubuntu3.6) to 2.14.1-0ubuntu3.7
apport-gtk (2.14.1-0ubuntu3.6) to 2.14.1-0ubuntu3.7
compiz (1:0.9.11.3+14.04.20141104-0ubuntu1) to 1:0.9.11.3+14.04.20150122-0ubuntu1
compiz-core (1:0.9.11.3+14.04.20141104-0ubuntu1) to 1:0.9.11.3+14.04.20150122-0ubuntu1
compiz-gnome (1:0.9.11.3+14.04.20141104-0ubuntu1) to 1:0.9.11.3+14.04.20150122-0ubuntu1
compiz-plugins-default (1:0.9.11.3+14.04.20141104-0ubuntu1) to 1:0.9.11.3+14.04.20150122-0ubuntu1
gir1.2-gudev-1.0 (1:204-5ubuntu20.9) to 1:204-5ubuntu20.10
libcompizconfig0 (1:0.9.11.3+14.04.20141104-0ubuntu1) to 1:0.9.11.3+14.04.20150122-0ubuntu1
libdecoration0 (1:0.9.11.3+14.04.20141104-0ubuntu1) to 1:0.9.11.3+14.04.20150122-0ubuntu1
libfreetype6 (2.5.2-1ubuntu2.2) to 2.5.2-1ubuntu2.3
libgudev-1.0-0 (1:204-5ubuntu20.9) to 1:204-5ubuntu20.10
liblightdm-gobject-1-0 (1.10.3-0ubuntu2) to 1.10.4-0ubuntu2
libpam-systemd (204-5ubuntu20.9) to 204-5ubuntu20.10
libsystemd-daemon0 (204-5ubuntu20.9) to 204-5ubuntu20.10
libsystemd-journal0 (204-5ubuntu20.9) to 204-5ubuntu20.10
libsystemd-login0 (204-5ubuntu20.9) to 204-5ubuntu20.10
libudev1 (204-5ubuntu20.9) to 204-5ubuntu20.10
lightdm (1.10.3-0ubuntu2) to 1.10.4-0ubuntu2
python3-apport (2.14.1-0ubuntu3.6) to 2.14.1-0ubuntu3.7
python3-problem-report (2.14.1-0ubuntu3.6) to 2.14.1-0ubuntu3.7
systemd-services (204-5ubuntu20.9) to 204-5ubuntu20.10
udev (204-5ubuntu20.9) to 204-5ubuntu20.10
x11-common (1:7.7+1ubuntu8) to 1:7.7+1ubuntu8.1
xorg (1:7.7+1ubuntu8) to 1:7.7+1ubuntu8.1
xserver-xorg (1:7.7+1ubuntu8) to 1:7.7+1ubuntu8.1
xserver-xorg-input-all (1:7.7+1ubuntu8) to 1:7.7+1ubuntu8.1
xserver-xorg-video-all (1:7.7+1ubuntu8) to 1:7.7+1ubuntu8.1



```

---

### Post by valvegrid on 2015-02-19
Found out what was what was wrong from a friend who uses Ubuntu.

---

