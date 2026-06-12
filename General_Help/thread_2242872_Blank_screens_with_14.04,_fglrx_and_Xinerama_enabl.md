---
title: "Blank screens with 14.04, fglrx and Xinerama enabled"
date: 2014-09-04
forum: General Help
---

### Post by ben106 on 2014-09-04
I recently did a fresh install of 14.04 on my machine running 2 (different) AMD graphics cards.  I installed the fglrx driver suite via the installer on AMD's website. I was able to get all 3 monitors working but then when I try enabling Xinerama, upon bootup after the Grub menu I see the Kubuntu loading screen and then all monitors go black.  If I boot up into recovery mode and remove the "Xinerama" "on" line from xorg.conf I am able to login normally.  

I have a Radeon HD 7850 and some other low-end AMD card (backup monitors).  I have tried both the 14.4 and the 14.6 drivers from AMD.  I can provide whatever output will help.

---

### Post by ben106 on 2014-09-05
Not really a fix, but here is what I've done now. 

I reinstalled with 12.04 (previous install had been messed up too much I felt), then had to swap video card slots since the primary card wasn't really in the "primary" slow on the mobo. I reinstalled the lastest stable AMD driver, 14.4 and then rebooted. I wasn't able to get 3 separate displays as you would normally think about it but I was able to get 2 monitors on the second display in a muli display setup (one xsession or whatever it's called for both). Since those 2 monitors are smaller than my primary which is in the middle it's a little annoying because I put the primary monitor above the other 2. Once I get a wall mount for my primary monitor (actually a TV) I'll be able to have it physically match the logical layout of the monitors in the AMD CCC.

---

