---
title: "Mounting NTFS drive."
date: 2008-05-24
forum: General Help
---

### Post by Kayos02 on 2008-05-24
I have a WD 180 gig NTFS drive, and is apparently labeled as /dev/sdb from what I've gathered. I've been trying to Google how to get this thing mounted, I have ntfs-3g set to allowing ntfs drives to be write enabled on boot if it matters.

The output of fdisk -l is the following: 

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55ff5348

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 180.0 GB, 180045766656 bytes
255 heads, 63 sectors/track, 21889 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?       13578      119522   850995205    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sdb4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

That's the information I know, I am trying to google it and figure it out but I am failing.

Any help is appreciated.

---

### Post by Zoja on 2008-05-24
try this way :

cd /media
sudo mkdir Data

and now (ver1):
sudo mount -t ntfs /dev/sdb /media/Data

or (ver2):
sudo mount -t ntfs /dev/sdb1 /media/Data

ver2 is due to the "hard to figure out" partition table you've got there .. hope it helps in some way . I've got a NTFS partition and mounting it this way works both to read and write on it so wish you luck and have fun :)

---

### Post by Kayos02 on 2008-05-24
You sir are a hero.

---

### Post by Zoja on 2008-05-25
indeed .. cheers lad ;)

---

### Post by digitaltailor on 2010-08-30
> **Zoja said:**
> try this way :

cd /media
sudo mkdir Data

and now (ver1):
sudo mount -t ntfs /dev/sdb /media/Data

or (ver2):
sudo mount -t ntfs /dev/sdb1 /media/Data

ver2 is due to the "hard to figure out" partition table you've got there .. hope it helps in some way . I've got a NTFS partition and mounting it this way works both to read and write on it so wish you luck and have fun :)

This worked great for me in xubuntu 9.10, but I wanted to know what I would put in fstab to get this to automount on startup.  Here is my current info.

/dev/sda4 mounting to /media/Data

I've tried a few things but I seem to have the wrong syntax.  I downloaded a GUI utility  to do this, but it totally wiped out my fstab (which I currently have automounting an NFS share from another machine).  Luckily I backed up my fstab before this program screwed it up, so restoring it wasn't a problem.  Any help would be greatly appreciated.

---

