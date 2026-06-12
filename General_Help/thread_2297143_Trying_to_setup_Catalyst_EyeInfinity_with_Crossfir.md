---
title: "Trying to setup Catalyst EyeInfinity with Crossfire on Ubuntu 15.04"
date: 2015-10-01
forum: General Help
---

### Post by andrew.coughlin@gmail.com on 2015-10-01
Trying to setup my EyeInfinity Crossfire setup on Ubuntu 15.04.  I have 2 HDD 6950 ATI cards, with the crossfire connection.  Mind you I had this working on Windows so I know the cards work fine.  I install the Catalyst control center and it complains that no AMD Drivers are installed.  If I try to install the additional drivers (I know when I go into additional drivers I have three selections, the one that is already selected and 2 others, I'm waiting for my reinstall to complete to get the other two selections) and reboot I get 5 red dots and it seems that ubuntu stops loading.  At this point the only thing I can do is reinstall to get it working again.  I don't get a the grub loader at all.  

I have read that people have gotten this working, but I wonder if anyone has gotten this to work in 15.04.  I have 14.X available if I need to try that.

---

### Post by andrew.coughlin@gmail.com on 2015-10-01
So the choices I have are Using X.Org X Server - AMD/ATI display driver wrapper from xserver-xorg-video-ati(open source, tested)
Using Video driver from the AMD graphics accelerators from fglrx (proprietary)
Using Video driver from the AMD graphics accelerators from fglrx-updates (properietary).

I believe the last time I selected something it was from fglrx and not the fglrx-updates.

---

### Post by andrew.coughlin@gmail.com on 2015-10-01
So it appears the fglrx drivers from ATI is causing the problem, I was able to recover from it by going into rescue mode and removing the .deb files and my machine started up fine.  Anyone have any experience setting this up?

---

### Post by oldos2er on 2015-10-01
Moved to General Help.

---

### Post by andrew.coughlin@gmail.com on 2015-10-02
So after doing some digging when the screen locks up press CTRL+ALT+F1 or F2, and login this way you then uninstall what you installed:

1. dpkg -l | grep 'fg'  <-- this lists all packages for fglrx
2. dpkg -r <packagename> <- do this for each package you installed before the reboot.
3. sudo apt-get install xserver-xorg-video-ati.
4. sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-org-core.
5. sudo dpkg-reconfigure xserver-xorg
6. Reboot.

You can also look at /var/log/Xorg.0.log and do a grep for EE and see if the problem is because the install didn't install in the location it should have.

In my case I contacted ATI and waiting for a reply.

Hopes this helps someone else.

---

