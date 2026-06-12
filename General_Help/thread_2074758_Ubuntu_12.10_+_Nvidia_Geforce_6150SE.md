---
title: "Ubuntu 12.10 + Nvidia Geforce 6150SE"
date: 2012-10-22
forum: General Help
---

### Post by JF382 on 2012-10-22
I recently installed Ubuntu 12.10 on my desktop, it has a Nvidia Geforce 6150SE Graphics Card. I can't even go to the Dash menu without the computer freezing. How would I go upon installing this driver without getting to the dash? Is it even possible? I know that this desktop worked with Ubuntu 12.04 just fine, hopefully someone can assist me through this. Does anyone else our their have the same graphics card? If so did you get Ubuntu 12.10 running with it? Thanks!

---

### Post by dino99 on 2012-10-22
the solution for that (such) card is to forget unity and the likes (GS) as they need more power.
boot in recovery mode and :

sudo apt-get purge unity
sudo apt-get purge compiz
sudo apt-get install gnome-session-fallback
sudo apt-get install lightdm-gtk-greeter

then reboot and login as gnome-classic

---

### Post by Favux on 2012-10-22
Hi JF382,

I have the 6150 Go and that hasn't worked for a while.  That is because nouveau is used by default and there is a bug that causes a 2 GB RAM limit.  Don't think that affects your card, so it is likely something else.  You can disable nouveau with the **nomodeset** kernel parameter so Quantal is forced to use the VESA driver.  That should let you get to Additional Drivers and install the Nvidia proprietary driver.

If you see the Grub2 menu when you boot arrow to the 3.5 kernel Quantal is using and hit the e key.  Otherwise hold down the left shift key during boot so the menu appears.  Edit the kernel boot line to add nomodeset.  Look for:
```
"quiet splash"
```
and change it to:
```
"quiet splash nomodeset"
```
This way of editing the kernel boot parameters is onetime and won't affect another boot unless you redo it.

---

### Post by ouff on 2012-12-20
I'm having a similar problem, though I can usually launch the dash.  It just takes FOREVER to load, and will freeze my computer about 1 out of every 10 times.  I have already tried the nvidia-current driver and the nvidia-current-updates driver.  Both of them made my computer even more unstable than xserver-xorg-video-nouveau.  This computer also worked just fine under 12.04 with Compiz enabled, so I don't want to remove unity or compiz unless there really is no other solution.  Anyone have any ideas?

Thanks in advance!

---

