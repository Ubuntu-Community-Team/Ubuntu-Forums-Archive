---
title: "Grub wont load Windows...."
date: 2007-03-09
forum: General Help
---

### Post by azazel00 on 2007-03-09
I just reinstalled my computer. I had to install linux first, due to some problems with my windows partition (I was hoping to get the windows data from ubuntu).

I then installed windows and configured grub to what should have been able to boot windows.

But instead of loading it, it get's stuck saying: ```
Starting up...
```

Here's the output from 'fdisk -l'```
Disk /dev/hda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1           14470       14596     1020127+  82  Linux swap / Solaris
/dev/hda2               1       14469   116222211   83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

```

And here is my 'menu.lst'
```
title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot


title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1
```

What could be causing this problem? If I change the drive boot order in the BIOS I can log into Windows just fine. But If the linux drive is set to boot first, I get stuck waiting for it to start.

Regards,
az

---

### Post by llamakc on 2007-03-09
After installing Windows did you JUST edit menu.lst, or did you follow the 'recover grub after installing Windows' path?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by azazel00 on 2007-03-09
Just edited it...

Didnt know there was some special surgery that had to be performed.

---

### Post by llamakc on 2007-03-09
Yeah, if you had installed Windows first, Ubuntu would have respected its install (provided you don't format the drive) and added a grub entry for you.

That link should hook you right up though. Good luck.

---

