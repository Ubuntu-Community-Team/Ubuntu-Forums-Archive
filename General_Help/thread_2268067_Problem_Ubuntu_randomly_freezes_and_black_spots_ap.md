---
title: "Problem: Ubuntu randomly freezes and black spots appear"
date: 2015-03-05
forum: General Help
---

### Post by dunmireg on 2015-03-05
Has anyone encountered this problem? Sometimes Ubuntu seems to "crash" and all text disappears. This includes browser and menus. Black spots appear in the upper left corner. It looks like this: [ATTACH=CONFIG]260480[/ATTACH]

I am running 14.04 and fully updated. Not sure what is going on. Thank you

---

### Post by v3.xx on 2015-03-06
Is this a new install?

Please post
```
uname -r && lspci | grep VGA && free -m
```

---

### Post by dunmireg on 2015-03-06
It is not a new install. I installed about a year ago and this problem has only cropped up in the past 3 months or so. Here's the output: 

3.13.0-46-generic
01:00.0 VGA compatible controller: NVIDIA Corporation GK106 [GeForce GTX 650 Ti] (rev a1)
             total       used       free     shared    buffers     cached
Mem:          7925       1303       6622         10         54        654
-/+ buffers/cache:        595       7330
Swap:         8130          0       8130

---

### Post by v3.xx on 2015-03-07
A couple ideas ..

Could a driver update help?  What driver are you running?
```
dpkg -l | grep nvidia
```
Also see if a crash report was generated in /var/crash/.

Can you run the Guest Account to see if it will crash?

You say browser and menu crashed.  Do other apps display ok?

We don't have much to go on :(

---

### Post by dunmireg on 2015-03-07
Here is the driver output: 

rc  nvidia-304                                            304.116-0ubuntu0.0.1                                amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                                         1:0.2.91.7                                          amd64        transitional package for ubuntu-drivers-common
ii  nvidia-settings                                       331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graph


There was no crash report generated. I'm sorry I didn't explain well. It doesn't always have this error, there doesn't seem to be anything that I do that specifically causes it (say launching a particular application). 

All the apps on my system are affected. So for example, if I go to the file tab no text will appear. Same with other tabs or even the menu on the settings gear. 

It's as if all text just gets wiped out totally throughout my machine.

---

### Post by v3.xx on 2015-03-08
From what I have been reading [HERE,]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GeForce+GTX+650+Ti+driver&sa=Search&cof=FORID:9") you should be running the same driver as I am.
[ATTACH=CONFIG]260518[/ATTACH]
I don't know if this will help, but is all I have to offer.

---

### Post by dunmireg on 2015-03-08
Thanks, I will make sure that is the driver I have. Thank you for your help!

---

