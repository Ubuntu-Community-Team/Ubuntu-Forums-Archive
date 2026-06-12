---
title: "How can I expand my filesystem space after installing ubuntu with Wubi?"
date: 2008-04-26
forum: General Help
---

### Post by ezekielnin on 2008-04-26
Hi,

I wanted to test if HH was working good on my machine so I installed it on 6gb using wubi. The thing is, IT WORKS AWFULLY WELL and I fell in love with it ... Now I'm thinking of using it a lot more so I would like to expand my 6gb virtual file system to something like 15gb ... is there a way to do this or do I have to uninstal wubi again and reinstall it?

thanks a bunch!

---

### Post by bodhi.zazen on 2008-04-26
See if this helps you.

If you are very new to Linux it may be easier to remove wubi, partition your hard drive, and re-install ubuntu to it's own partition.

[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

---

### Post by _sAm_ on 2008-04-26
Guide for it here: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

When using wubi you must use FAT32 right? Well, the Linux filesystem ext3 is much better, and will not make the OS slower over time as FAT cus fragmented drive. So I would followed bodhi.zazen advice. It is not hard to install Ubuntu in dualboot with Windows:-)

---

### Post by ezekielnin on 2008-04-26
Thanks,

I'll check the wubi guide. But the wubi install doesn't use the Fat32 file system. The reason why I choosed wubi is not because the installation process is easier but really because the uninstall process is FAR easier. I don't like grub.

---

### Post by bodhi.zazen on 2008-04-26
FYI : Wubi installs into a file which is used by Ubuntu as a "hard drive" I believe using LVM and a linux file system.

Second if you do not want to use grub, you will need to know how to configure the windows boot loader. of the two, grub is more versatile and, IMO, easier to configure.

---

### Post by ezekielnin on 2008-04-26
Effectively : > **How do I get rid of the virtual disks and switch to real partitions, and/or get rid of Windows entirely?**

Existing Wubi/Lubi 7.04/7.10 installations can be upgraded to a full, real ubuntu install with dedicated partitions using LVPM. The main site for LVPM is at [WWW] [http://lubi.sourceforge.net/](http://lubi.sourceforge.net/) and the guide and support forum is at [WWW] [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591). LVPM does not yet work with Wubi 8.04. 

I'll wait until LVPM works with 8.04 ... until then I'll continue to use wubi. 

> of the two, grub is more versatile and, IMO, easier to configure. 

still, it is a pain in the a-- to uninstall.

---

### Post by bodhi.zazen on 2008-04-26
Removing grub is very easy. boot your windows CD and use fixbmr from the restore console.

If you do not have a windowsdisk there are several solutions including restoring it from Ubuntu.

---

### Post by ezekielnin on 2008-04-26
Oh, you mean with a windows XP CD? I didn't know it was that easy....

so hum ... if the wubi install went without any issue it should be the same with a an normal ubuntu install?

---

### Post by AldenIsZen on 2008-04-26
> **ezekielnin said:**
> Oh, you mean with a windows XP CD? I didn't know it was that easy....

so hum ... if the wubi install went without any issue it should be the same with a an normal ubuntu install?

I like the live disks of Ubuntu and while this is my first experience with an OS that did that, they didn't pioneer it. Anyhow, I like to keep one around and try not to give away my last one in case I do something bad and can't boot into anything. I use **_*[Super Grub Disk]("http://www.supergrubdisk.org/")*_** and it can easily enough fix your GRUB in the MBR or can make it go back to the way it was and load windows straight away, effectively hiding your Ubuntu setup. If you want to get rid of the Ubuntu partition, then just use a ***_[G-Parted live CD]("http://gparted.sourceforge.net/livecd.php")_***. If I recall G-Parted is what is used in Ubutu by default. But they have a live CD. All in all very simple and a lot less pain than Windows experience and fixes imho.

---

### Post by ezekielnin on 2008-04-26
@ AldenIsZen - Thanks for these 2 tools. I'll use them.

---

