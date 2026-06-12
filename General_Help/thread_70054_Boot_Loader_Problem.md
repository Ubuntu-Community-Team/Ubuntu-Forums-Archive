---
title: "Boot Loader Problem"
date: 2005-09-28
forum: General Help
---

### Post by Ryu-Chan on 2005-09-28
Hi, I'm new here and I know this probably has been posted a million and one times before, but I couldn't fix the problem myself by looking through the forum.

Anyway, my problem is I have 2 hard drives. One hard drive is a normal IDE ATA with Ubuntu installed, and the other is a SATA with Windows xp installed. I cannot edit the menu.lst file for grub correctly to get it to load into Windows. I'll enter root  (sda0,0) and it'll tell me that it cannot parse the numbers correctly. I did an fdisk -l and it came up with this:


Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14616   117402988+  83  Linux
/dev/hda2           14617       14946     2650725    5  Extended
/dev/hda5           14617       14946     2650693+  82  Linux swap / Solaris

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30514   245103673+   7  HPFS/NTFS

My main problem is that I don't know what half this data means. I'm new to linux and I'm just getting use to the terminal and installing stuff. This is what's in my menu.lst so far:

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

title	Windows XP
root	(sda0,0)
makeactive
chainloader	+1

Any help would be much appreciated. Thanks.

---

### Post by tomchuk on 2005-09-28
try this:
```

title Windows XP
rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
makeactive
chainloader +1

```

---

### Post by Ryu-Chan on 2005-09-29
That worked for the most part, but now when it begins to load windows it says an NT component is missing. I don't remember exactly which one it said, but it was NTDIR or something along those lines.

EDIT: Never mind, I figured it out for myself. Thanks for the help.

---

