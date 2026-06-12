---
title: "[Solved] Kinit: No resume image"
date: 2008-01-08
forum: General Help
---

### Post by Peter Sommer-Larsen on 2008-01-08
This worked for me:

$ sudo aptitude install update-usplash-theme usplash-theme-ubuntu
$ sudo nano /etc/usplash.conf
-----------------------------------------
# Usplash configuration file
xres=1024
yres=768
-----------------------------------------
$ sudo update-usplash-theme usplash-theme-ubuntu

---

### Post by ianderthal on 2008-01-16
Thank you so much for solving this problem!

---

### Post by hegenious on 2008-02-10
Thanks so much indeed... It solved an annoyance I have been researching for weeks :KS

---

### Post by Jojan on 2008-02-18
I think I turned off my computer weird an now I get the message
> [FONT="Courier New"]Start up ...
Loading, please wait...
usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864 failed
usplash:Using mode 1024x768
kinit: bane_dev_to_t(/dev/disk/by-uuid/ (alot of numbers + some letters) ) = Sda5(8,5)
kinit: trying to resume image from /dev/disk/by-uuid/ (same as above)
kinit: No resume image, doing normal boot...[/FONT]

I tried to "sudo aptitude install update-usplash-theme usplash-theme-ubuntu" but they weren't found.
So what should I do?

---

### Post by Jojan on 2008-02-19
bump

---

### Post by Jojan on 2008-02-20
Solved: Reinstallation.

Found other posts around the Internet with the same problem. I managed to backup the most important stuff thanks to a Live CD.

---

### Post by Davhoe on 2008-02-26
Sorry for being a noob. but how do I close GNU nano? 

Thanks.

---

### Post by Dennis on 2008-02-26
> Sorry for being a noob. but how do I close GNU nano?


Ctrl x

---

### Post by Davhoe on 2008-02-26
> **Dennis said:**
> Ctrl x

Thanks much. When I go to save it, it comes up with directory not found. I installed it, so why isn't it working?

---

### Post by Jojan on 2008-03-08
I got the same error thing again and now
```
sudo dpkg-reconfigure xserver-xorg
```
worked just fine.

---

### Post by chappejw on 2008-05-15
I was facing this similar issue after trying to set up a dual monitor configuration with my Toshiba a100 laptop and a 17" Samsung 730B LCD on Ubuntu 8.04. After messing around with my screen resolution and trying to configure an extended desktop, something crashed and I likely botched my video driver settings. 

Each time I would boot up I would have a low resolution warning and 3 options in a pop up box. Continue, Re-configure, or shutdown. Reconfiguring it each time didn't seem to work so to fix the issue completely without much effort this is what I did to fix it.

1. Reboot the system and press 'esc' while booting up

2. choose 'single user mode' or 'recovery mode'

3. after doing this Ubuntu recognized that my video card and monitor were not being 
   recognized so it gave me an option to re-detect my hardware and set everything 
   back to system recommended settings.

4. Fixed! My laptop is again working perfectly thanks to Ubuntu. And only under 
   Ubuntu I might add.

---

