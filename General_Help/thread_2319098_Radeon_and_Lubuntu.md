---
title: "Radeon and Lubuntu"
date: 2016-04-01
forum: General Help
---

### Post by asearle on 2016-04-01
Hallo Everyone,

I am running Lubuntu 14.04 on a Samsung Series 5 "ultrabook"-style laptop with a AMD A6-4455M APU (x2) and Radeon HD 7500G graphics card/device.  But, ever-since I have had the unit (several years now), I have experienced short battery life (about one hour) and overheating.  At various times I felt that this was maybe caused by the AMD/ATI Trinity Radeon HD 7500G graphics and have installed and de-installed various permutations of drivers.  I currently have the following installed ...

xserver-xorg-video-ati
libdrm-radeon1
xserver-xorg-video-radeon
fglrx-amdcccle
fglrx
libdrm-radeon1:i386
fglrx-core

... but still get the short battery-life and the overheating.

Does anyone have an idea?  Is it the graphics card?  Or maybe something else?  Maybe the AMD-processor?

And how is it with Lubuntu?  I really love the menu-structures and handling of Lubuntu but can Lubuntu/LXDE handle the Radeon graphics card?  I also read that Lubuntu is not as well supported as Ubuntu itself so should I be looking around for a change (e.g. to Ubuntu)?  I really hope not.

Many thanks for any tips that you can give me.

Regards,
Alan

---

### Post by mörgæs on 2016-04-01
> **asearle said:**
> 
Can Lubuntu/LXDE handle the Radeon graphics card?


Yes, the drivers are the same throughout the Buntu family.

> **asearle said:**
> 
I also read that Lubuntu is not as well supported as Ubuntu itself.


Links, please.

A boot parameter may or may not be necessary:
[https://help.ubuntu.com/community/RadeonDriver#Ubuntu_12.04.5_LTS_.28Linux_kernel_3.13.0.29.2C_Ubuntu_14.04_LTS_and_later](https://help.ubuntu.com/community/RadeonDriver#Ubuntu_12.04.5_LTS_.28Linux_kernel_3.13.0.29.2C_Ubuntu_14.04_LTS_and_later)

---

### Post by BazBear on 2016-04-01
> **asearle said:**
> Hallo Everyone,

I am running Lubuntu 14.04 on a Samsung Series 5 "ultrabook"-style laptop with a AMD A6-4455M APU (x2) and Radeon HD 7500G graphics card/device.  But, ever-since I have had the unit (several years now), I have experienced short battery life (about one hour) and overheating.  At various times I felt that this was maybe caused by the AMD/ATI Trinity Radeon HD 7500G graphics and have installed and de-installed various permutations of drivers.  I currently have the following installed ...

xserver-xorg-video-ati
libdrm-radeon1
xserver-xorg-video-radeon
fglrx-amdcccle
fglrx
libdrm-radeon1:i386
fglrx-core

... but still get the short battery-life and the overheating.

Does anyone have an idea?  Is it the graphics card?  Or maybe something else?  Maybe the AMD-processor?

And how is it with Lubuntu?  I really love the menu-structures and handling of Lubuntu but can Lubuntu/LXDE handle the Radeon graphics card?  I also read that Lubuntu is not as well supported as Ubuntu itself so should I be looking around for a change (e.g. to Ubuntu)?  I really hope not.

Many thanks for any tips that you can give me.

Regards,
AlanHave you tried installing the [TLP]("http://linrunner.de/en/tlp/tlp.html") power management tool? I can't personally vouch for it, but other people seem to have good results using it.

---

