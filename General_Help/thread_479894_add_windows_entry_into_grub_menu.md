---
title: "add windows entry into grub menu"
date: 2007-06-20
forum: General Help
---

### Post by marcelocr2 on 2007-06-20
Hi, i installed ubuntu 6.06 after installing vista and the grub doesn show vista so i cant boot it..
i list my partition table and it shows this
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        6719    52428800    7  HPFS/NTFS
/dev/sda3            6720       12161    43712865    5  Extended
/dev/sda5            6720       12008    42483861   83  Linux
/dev/sda6           12009       12161     1228941   82  Linux swap / Solaris
```

i know i have to edit /boot/grub/menu.lst and iim not sure how im supposed to add the next lines

```

title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

my problem is that i dont know what i have to write instead fo root (hd0,0) because my windows partition is in /dev/sda2
thank you

---

### Post by merlinus on 2007-06-20
Try:
> 
rootnoverify (hd0,1)

because windows is the second partition on your hard disk.

-merlin

---

