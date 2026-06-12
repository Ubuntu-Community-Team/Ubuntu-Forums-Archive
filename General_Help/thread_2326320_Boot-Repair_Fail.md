---
title: "Boot-Repair Fail"
date: 2016-05-30
forum: General Help
---

### Post by 1.fetus.boygmail. on 2016-05-30
Hello,



I was screwing around with the Linux video card drivers and the proprietary drivers trying to get Steam to work to play some Tomb Raider and selected proprietary driver and...BAM, daddy jacked his system. I restarted my system it did its normal business loaded a purple background with Ubuntu and then a black screen with a worrying flashing possible demonic underscore.  I tried to fix it through recovery mode via "Drop to root shell prompt" and mount -o remount, rw /. That didn't do anything so I tried to install with USB ISO, but provided no options to repair or reinstall without deleting all my files/documents. So finally I did a boot repair, the information is at [http://paste.ubuntu.com/16845683/](http://paste.ubuntu.com/16845683/).  If you could provide me any information on how to proceed, or a therapist it would be greatly appreciated. I'm not brand new to Linux, I have been breaking systems for years.

Sincerely,


Jumping Jimmy Joe Jo Johnson (J 2 the 5th power)
But some people call me...Tim
Random emoji's #-o#-o:D:popcorn:...so true.

---

### Post by grahammechanical on 2016-05-30
> "Drop to root shell prompt" and mount -o remount, rw /.

That puts the file system (partition) into read/write mode. Which is necessary if we are going to use root shell prompt to run commands that write to the file system.

Boot Repair will re-install the boot loader (Grub) but the boot loader was doing its job. The problem happened after the boot loader loaded Linux. And this was caused by 

> selected proprietary driver and...BAM, daddy jacked his system.

So, it is some kind of conflict with a proprietary video driver. Boot repair does not fix proprietary video driver problems. It seems to me that you need to remove or purge the proprietary video driver and by doing so revert to using the open source video driver so that you can get to a working desktop where you can begin again.

Grub boot menu>Advanced options for Ubuntu>Recovery mode kernel>Recovery menu>Resume. That will some times get us to a working desktop using a fall back open source video driver. From there it is System Settings>Software & Updates>Additional Drivers tab.

You do not tell us what make of video card you have. So, we cannot tell you how to use Root shell prompt to purge a proprietary video driver. You do not tell us what version of Ubuntu you are using. That may have a factor in this problem. Especially if it is an AMD card with Ubuntu 16.04.

Did you use Additional Drivers to install this proprietary video driver? Or was it a video driver downloaded from some web site?

Regards.

---

