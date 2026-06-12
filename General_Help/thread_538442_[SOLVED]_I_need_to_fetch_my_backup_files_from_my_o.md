---
title: "[SOLVED] I need to fetch my backup files from my old Windows HD"
date: 2007-08-30
forum: General Help
---

### Post by mahasmb on 2007-08-30
I was on a dual-boot 120 GB HD with both partitions having Windows XP on them. I started having problems with my primary partition, so I  backed up all my files onto a 40 GB HD that was lying around.

I installed Feisty Fawn successfully, but my second Windows XP partition on the 120 GB HD won't boot. I can still access the files though.

What's most important to me right now is being able to fetch my files from the 40 GB HD. I have it connected to my PC, and it shows it's connected but it only shows up as "New Volume". Feisty can tell me how much space it's using but I can't even look at the files in them.

Whenever I try to click on the icon for the "New Volume" drive, a dialog box pops up saying 

> **"Cannot mount volume.**
Invalid mount option when attempting to mount the volume "New Volume'.

How can I access these files? I know Windows can see them. But Ubuntu doesn't seem to be able to see the files.

"fdisk -l" gives this
```
maha@maha-dlu:~$ sudo fdisk -l

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   ?      216399     1904881   850995205    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hdb2   ?      723265     1262922   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hdb3   ?      167316      167316           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/hdb4         2671568     2671619       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1          93      746991   82  Linux swap / Solaris
/dev/hdc2           10444       14945    36162315    f  W95 Ext'd (LBA)
/dev/hdc3              94       10443    83136375   83  Linux
/dev/hdc5           10444       14945    36162283+   7  HPFS/NTFS

Partition table entries are not in disk order

```

Please help. I have no idea what to do.

---

### Post by koobert637 on 2007-08-30
try mounting from the command line

mount -t vfat /dev/hdb /mnt
cd /mnt
ls

if you can see your files try navigating to /mnt from nautilus and access your backups

---

### Post by mahasmb on 2007-08-30
I get the following error

```
maha@maha-dlu:/mnt$ sudo mount -t vfat /dev/hdb /mnt
mount: wrong fs type, bad option, bad superblock on /dev/hdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by koobert637 on 2007-08-30
how about mount -t ntfs /dev/hdb1 /mnt ?

---

### Post by merlinus on 2007-08-30
From what I see, ubuntu is telling you that your partition table is defective.  That is why you cannot mount that disk.

You might try using this tool to fix it:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

-merlin

---

### Post by splintercellguy on 2007-08-30
No, he's mounting the wrong device. He should mount /dev/hdbx, x being whatever number the device partition is.

---

### Post by bodhi.zazen on 2007-08-30
> **splintercellguy said:**
> No, he's mounting the wrong device. He should mount /dev/hdbx, x being whatever number the device partition is.

That and I do not see a vfat partition.

mahasmb, are you trying to mount a ntrs partition ?

In that event :

mount /dev/hdbx /mnt

or 

mount -t ntfs /dev/hdbx /mnt

Which partition are you wanting to mount ?

---

### Post by mahasmb on 2007-08-30
> **merlinus said:**
> From what I see, ubuntu is telling you that your partition table is defective.  That is why you cannot mount that disk.

You might try using this tool to fix it:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

-merlin
**THANK YOU!**

I had so much trouble figuring out how to use this program, but as we speak, I'm copying over some of my files. So it looks like it's working great so far!

Bodhi: Like I said, this was an old HDD that I found lying around. I reformatted it in Windows XP to an NTFS partition (Just by right clicking "Format Drive" while in Windows). I did not install any OS on it. I just reformatted the hard disk drive and then copied over my files.

---

### Post by mahasmb on 2007-08-31
I was able to copy over all my files from the 40 GB HDD to my 120 GB HDD. Now I'm wondering, how can I get my Windows XP on my 120 GB HDD to boot up again?

Would something like this ([http://www.kellys-korner-xp.com/win_xp_rec.htm](http://www.kellys-korner-xp.com/win_xp_rec.htm)) help me or make things worse?

---

### Post by mahasmb on 2007-09-05
Anyone?

---

### Post by merlinus on 2007-09-05
You can use the recovery console to restore xp to the mbr (master boot record).  That will overwrite grub, however, so you will not be able to boot ubuntu until you restore it.

That can be done from the live cd.

-merlin

---

