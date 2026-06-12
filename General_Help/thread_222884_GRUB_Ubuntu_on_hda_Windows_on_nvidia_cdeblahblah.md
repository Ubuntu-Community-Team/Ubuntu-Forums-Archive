---
title: "GRUB: Ubuntu on hda Windows on nvidia_cdeblahblah"
date: 2006-07-25
forum: General Help
---

### Post by rmjb on 2006-07-25
Hi, I have Ubuntu installed on hda and Windows XP on a SATA RAID-0 that comes up as /dev/mapper/nvidia_cdeblahblah.

I want to put an entry into grub to boot my Windows so I went to the grub prompt and entered:

```
device (hd1) /dev/mapper/nvidia_cdeblahblah
```

But when I exited that and looked at my device.map file it still had:

```
(hd0) hda
(hd1) sda
(hd2) sdb
```

So I erase the last two lines and add (hd1) as my SATA RAID device.

Then I go to menu.lst and put an entry for Windows that looks something like:

```
rootnoverify (hd1)
makeactive
chainload +1
```

When that didn't work I changed it to:

```
rootnoverify (hd1,0)
makeactive
chainload +1
```

But that didn't work either. Any ideas how I can get grub to load Windows?

P.S. I have dmraid installed already.

- rmjb

---

### Post by john_spiral on 2006-07-25
Pop in the ubuntu live cd.

(1) start a terminal and type (Applications>Accessories>Terminal):

sudo fdisk -l

it will list all your drives connected to the machine.

post this info here.

(2) Can you tell us what the drive boot order inside the CMOS is?

(3) Take a look at the /boot/grub/device.map on your ubuntu partition, it tells you what number your drive has been assigned.

start with (1) and move down.... good luck

---

### Post by rmjb on 2006-07-25
Well I booted Xubuntu (I gave away my Ubuntu CD) and the output of *sudo fdisk -l* is:

```
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5

Unable to seek on /dev/sda
```

I figure that's from my RAID-0

After I install **dmraid** I still get the same error, but if I run *sudo fdisk -l /dev/hda* I get:

```
Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        3352    26916907+   f  W95 Ext'd (LBA)
/dev/hda2            3353        4866    12161205   83  Linux
/dev/hda5               2        1786    14337981    7  HPFS/NTFS
/dev/hda6            1787        3091    10482381    7  HPFS/NTFS
/dev/hda7            3092        3352     2096451   82  Linux swap / Solaris
```

And *sudo fdisk -l /dev/mapper/nvidia_cfecdcbc* gives:

```
Disk /dev/mapper/nvidia_cfecdcbc: 164.6 GB, 164696553472 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_cfecdcbc1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/mapper/nvidia_cfecdcbc2            1531       20023   148545022+   f  W95 Ext'd (LBA)
/dev/mapper/nvidia_cfecdcbc5            1531        4080    20482843+   7  HPFS/NTFS
/dev/mapper/nvidia_cfecdcbc6            4081       16963   103482666    7  HPFS/NTFS
/dev/mapper/nvidia_cfecdcbc7           16964       19637    21478873+   7  HPFS/NTFS
/dev/mapper/nvidia_cfecdcbc8           19638       20023     3100513+   7  HPFS/NTFS
```

The boot order before Ubuntu had the RAID-0 first, after I installed Ubuntu on the single PATA drive (hda), that drive is first in the boot order on the CMOS.

My device.map had:

```
(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/sdb
```

But like I said I changed that to:
```

(hd0)   /dev/hda
(hd1)   /dev/mapper/nvidia_cfecdcbc
```

So my question is, how do I get GRUB to recognise the SATA RAID-0 and then boot to it?

- rmjb

---

### Post by john_spiral on 2006-07-28
try below in menu.lst:

title Windows XP
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

you might need to use the map commands,XP likes to think it's booting off first disk.

keep device.map as:

(hd0) /dev/hda 
(hd1) /dev/sda 
(hd2) /dev/sdb

---

### Post by john_spiral on 2006-07-28
see 2nd post on the following thread:

[http://www.ubuntuforums.org/showthread.php?t=114519&highlight=dual+boot+xp+raid](http://www.ubuntuforums.org/showthread.php?t=114519&highlight=dual+boot+xp+raid)

---

### Post by rmjb on 2006-07-28
That worked! Thanks.

I left my device.map to:
(hd0)   /dev/hda
(hd1)   /dev/mapper/nvidia_cfecdcbc

And it's working.

- rmjb

---

