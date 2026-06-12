---
title: "Another Grub Error 17 topic"
date: 2007-02-05
forum: General Help
---

### Post by Philder on 2007-02-05
Sorry, another Grub error 17 thread...have searched the others and still can't work out what's going on with mine.

Have my PC dual booting XP Pro and gNewSense, set up as follows :-

hda - XP (master)
hdb - gNewSense (slave)
hdd - 250gb NTFS "archive" for general storage

Upon booting, sometimes grub loads, whilst every so often I get Error 17. Seems to work fine on a cold boot after not being used for a while (eg first switch on when I get in from work of an evening), but any subsequent power on after that gives the Error 17. That said, immediate restarts work ok. Is it possible things aren't shutting down correctly at power off? Curiously, as and when I get the error, a reboot fixes the problem, so I'm really not sure what's going on? If Grub can see the partition but can't mount it, surely that should always be the case? How can the error be so random?

Here's the output of fdisk -l :-

Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot  Start         End      Blocks   Id  System
/dev/hda1   *       1        5004    40194598+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot  Start         End      Blocks   Id  System
/dev/hdb1   *     128        2221    16820055   83  Linux
/dev/hdb2           1         127     1020096   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot  Start         End      Blocks   Id  System
/dev/hdd1   *       1       30401   244196001    7  HPFS/NTFS

Bearing in mind I'm a bit new to this, the things that look odd to me are the "Partition table entries are not in disk order" message (based on what other people have posted) and hdd1 having what I'm assuming is some sort of bootable flag (*) given it's purely a storage device (internal). Other than that, I'm lost...

Here's menu.lst :-

menu.lst

title		gNewSense, kernel 2.6.15-27-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		gNewSense, kernel 2.6.15-27-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		gNewSense, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		XP PRO
root		(hd0,0)
savedefault
makeactive
chainloader	+1

There's doubtless something blindingly obvious in there, but I can't see it!

Any help appreciated, as I've spent the last year gradually moving off XP and I'm damned if this'll stop me!

Thanks

Phil

---

### Post by chalex on 2007-02-05
an intermittent error like this suggests a hardware fault.

Have you run memtest?

Have you run your HD manufacturer's diagnostics?

Do you have backups?

---

