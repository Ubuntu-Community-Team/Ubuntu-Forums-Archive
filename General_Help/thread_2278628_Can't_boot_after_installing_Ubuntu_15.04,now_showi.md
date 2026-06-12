---
title: "Can't boot after installing Ubuntu 15.04,now showing Gallium 0.4 instead of Intel HD"
date: 2015-05-18
forum: General Help
---

### Post by bimalgeorgethomas on 2015-05-18
My computer doesn't boot normally, I have to press F12 and then select HDD and then select safe mode. My laptop is running Ubuntu 15.04, Toshiba Satellite  C600-P4012. Intel Pentium T4500. Intel GL40 chipset. Intel HD  Graphics. In "About Computer" earlier it showed Intel HD Graphics,  instead it is now showing Gallium 0.4 on llvmpipe (LLVM 3.6, 128  bits). Now videos are playing real slow. 1024 x 768  (4:3) is the maximum setting in "Display". Battery is draining really fast. Please help.

---

### Post by austin35 on 2015-05-19
> **bimalgeorgethomas said:**
> My computer doesn't boot normally, I have to press F12 and then select HDD and then select safe mode. My laptop is running Ubuntu 15.04, Toshiba Satellite  C600-P4012. Intel Pentium T4500. Intel GL40 chipset. Intel HD  Graphics. In "About Computer" earlier it showed Intel HD Graphics,  instead it is now showing Gallium 0.4 on llvmpipe (LLVM 3.6, 128  bits). Now videos are playing real slow. 1024 x 768  (4:3) is the maximum setting in "Display". Battery is draining really fast. Please help.

Yes please help! I am having the same issue. my previous ubuntu installations worked fine, now i can only boot from recovery mode. But my computer is much older and slower. Its a Dell D410 Latitude, Ubuntu 15.04, Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller( its 11 years old, but still ran great) What can i do to change it?

---

### Post by monkeybrain20122 on 2015-05-19
Maybe kind of like this problem? [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1074779](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1074779)
See #18 for a work around.

Also [http://askubuntu.com/questions/183305/graphics-driver-being-reported-as-gallium-0-4-on-llvmpipe-llvm-0x300-instead-o](http://askubuntu.com/questions/183305/graphics-driver-being-reported-as-gallium-0-4-on-llvmpipe-llvm-0x300-instead-o)
and 
[http://askubuntu.com/questions/436374/how-to-get-rid-of-the-gallium-0-4-on-llvmpipe-llvm-0x300-driver-intel-needed](http://askubuntu.com/questions/436374/how-to-get-rid-of-the-gallium-0-4-on-llvmpipe-llvm-0x300-driver-intel-needed)

---

### Post by grahammechanical on 2015-05-20
Gallium 0.4 is what we see if we are using the nouveau open source video driver on a Nvidia video adapter. You do not mention that you have an Nvidia video adapter. Do you have hybrid graphics? Also known as Optimus Technology?

Ubuntu uses llvmpipe as a fall back open source video driver in three situations. 

a) During installation the video card is detected as not being able to do hardware accelerated 3D rendering. In other words, the card cannot run Unity 3D.
b) We load Ubuntu using Recovery Mode>Resume.
c) There is some sort of problem with proprietary video drivers.

A possible solution for both users with this problem is to go to System Settings>Software & Updates>Additional Drivers tab and change video drivers. In my case I am runing 15.04 on an older Nvidia card but I cannot use the latest Nvidia drivers because they no longer support my video adapter. I have to use a legacy (= older version) driver if I want to use a proprietary video driver.

Regards.

---

### Post by bimalgeorgethomas on 2015-05-21
Yesterday after an update my system is doing ok. Thank you for helping.

---

