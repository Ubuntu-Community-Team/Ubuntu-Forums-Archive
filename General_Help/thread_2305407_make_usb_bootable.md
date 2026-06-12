---
title: "make usb bootable"
date: 2015-12-05
forum: General Help
---

### Post by hurtstotalktoyou on 2015-12-05
I have an iso file which is supposed to be bootable as a usb flash drive, but when I extract the iso to my usb stick (formatted as FAT32) it refuses to boot.  I get the standard error *"This is not a bootable disk.  Please insert a bootable floppy and press any key to try again..."*

I have tried using gparted to flag the usb main partition as "boot".  Still no luck.

Is there some general method for getting a usb stick to be bootable?  All the google search results are for special cases, usually OS installation disks.

The iso I'm trying to make bootable is the Samsung srs4 "admin tool".  You see, I installed ubuntu on my Samsung NC10 netbook and now the recovery partition, although intact, will not load properly.  Supposedly, the srs4 admin tool will fix this, but I need to make it bootable before I can use it.  Everyone on the sammynetbook forum says that it shouldn't require any special methods---just extract using WinRAR (except I'm using 7zip instead).  It does not work for me.

Thanks guys!

---

### Post by QDR06VV9 on 2015-12-05
Have you tried this on creating bootable USB's
[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)

---

### Post by sudodus on 2015-12-05
Are you running the computer in BIOS mode or UEFI mode, and what about the the Samsung srs4 "admin tool"? Is it supposed to work in BIOS mode or UEFI mode or both?

---

