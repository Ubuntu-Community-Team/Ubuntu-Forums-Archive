---
title: "Help on installing GRUB to usb drive"
date: 2007-01-30
forum: General Help
---

### Post by geek_Man on 2007-01-30
Answering your questions...

**Q** Can I say that during boot, If i plug in my USB HDD, i get the boot menu (GRUB here) where I can choose Windows / Ubuntu... and If I dont plug in my USB drive during boot, the laptop silently loads up Windows XP??? 

**A** I have installed Ubuntu to my external hard drive and it works great. For a long time I tried to install GRUB to the external drive only, but it would always look in the wrong drive when trying to boot. I have not yet resolved this, so I've just installed GRUB on my internal hard drive.


**Q** I'm going to install Ubuntu onto my USB HDD. Is there going to be any, if at all, ANY effect on my internal HDD??? 

**A** No, as long as you're careful with the partitioner, it won't have any effect on Windows.


**Q** Can I have Ubuntu boot without GRUB installation??? 

**A** Yes, but you would *have* to have some way of booting it if you wanted to run it (which I'm sure you do). I.e., the Windows boot loader, Super GRUB Disk, or some other means.


**Q** If I have to install GRUB, will it affect the MBR on the internal drive containing windows???

**A** Not if you don't install it on that drive. If you do install GRUB on the MBR of the internal drive, then the Windows bootloader *will* be replaced.


Like I said, I haven't gotten GRUB to work on my external drive, so I've installed it on my internal one. I would recommend this, unless you disconnect the usb drive a lot. GRUB is also more flexible with other operating systems, as the Windows boot loader is not. You'd be able to put Windows in the GRUB menu along with Ubuntu and whatever else you might have. Hope this answers your questions, and I'll be glad to answer any more.

(To the mods: this is a reply to an e-mail I got, just so that you don't look at it and go "huh?".)

---

