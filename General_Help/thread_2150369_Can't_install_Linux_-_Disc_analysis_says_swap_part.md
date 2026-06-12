---
title: "Can't install Linux - Disc analysis says swap partition is misaligned by 1024 bytes"
date: 2013-05-31
forum: General Help
---

### Post by bipbipman on 2013-05-31
Hello

I am in deep despair. I was running windows 7 and Ubuntu in dual-boot. For some reason win 7 started to not load properly and after trying unsuccessfully a repair using my Samsung computer recovery tool I ended up trying to wipe it by doing a full install of Linux Mint. Linux Mint got installed apparently OK and then I attempted to install Ubuntu 12.04 as a replacement. The installer crashed with the following error message: 
**************
The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.
***************

When looking into disc analyzer, I have one large ext4 partition (sda1), one small swap (sda5) partition and one "container for logical partition" one (sda2). For this sda2 one, I have an error message saying "this partition is misaligned by 1024 bytes - this may result is very poor performance, repartioning is suggested" but I can't get it fixed. 

I can provide more info upon request but don't even know where to start. I can run LiveUSB but all Linux installers crashes.... Thanks in advance for your help!!!!!!!

Bipbipman

---

### Post by bipbipman on 2013-05-31
I forgot to mention that at some point I was able to run a boot repair that was unsuccessfull and returned the following message: [http://paste.ubuntu.com/5720488](http://paste.ubuntu.com/5720488)

---

