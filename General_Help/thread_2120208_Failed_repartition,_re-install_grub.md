---
title: "Failed repartition, re-install grub"
date: 2013-02-26
forum: General Help
---

### Post by mpgarate on 2013-02-26
I repartitioned my hard drive, and when I restarted Grub no longer worked. I am now on a live Ubuntu USB drive to run Gparted. Gparted shows my entire drive as "unallocated", but Ubuntu successfully mounts the drive and its partitions.

How do I go about restoring the partition structure / re-install GRUB?

---

### Post by carl4926 on 2013-02-26
Could you explain a little more
Perhaps include a screen of what you see in Gparted

---

### Post by mpgarate on 2013-02-26
This is what I see in Gparted:

[http://i.imgur.com/4xUILYf.jpg](http://i.imgur.com/4xUILYf.jpg)

However, the partitions on the device are mounted and browsable. I would like to install GRUB on this device and attempt to boot into my Ubuntu install. 

Is there a command I could run to list further useful information?

---

### Post by carl4926 on 2013-02-26
> but Ubuntu successfully mounts the drive and its partitionsPlease explain more...

From that image, you have no partitions

So are you saying that you can mount some partitions in Nautilus?

```
sudo fdisk -l
```lets see this too

---

### Post by mpgarate on 2013-02-26
Ubuntu automatically mounted all of the partitions in nautilus, and they appear on my left sidebar at the bottom. 

I am now attempting to restore the filesystem using GParted's gpart feature.

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x12790f7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2459647     1228800    7  HPFS/NTFS/exFAT
/dev/sda2         2459648   591222239   294381296    7  HPFS/NTFS/exFAT
/dev/sda3       591222240  1400550479   404664120    7  HPFS/NTFS/exFAT
/dev/sda4      1400555519  1465147391    32295936+   f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5      1400555520  1448747007    24095744   83  Linux
/dev/sda6      1448747008  1465147391     8200192   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 8029 MB, 8029470208 bytes
34 heads, 17 sectors/track, 27132 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x31a43a44

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15681535     7839744    b  W95 FAT32
ubuntu@ubuntu:~$ 


```

---

### Post by carl4926 on 2013-02-26
I don't feel sure enough to advise a course of action. It looks like the partition table has been corrupted.
But regardless, the first thing I would do (if that is possible for you) is to copy any data I can't afford to loose, over to a external HD)

Check this thread
[http://ubuntuforums.org/showthread.php?t=2118759&page=2](http://ubuntuforums.org/showthread.php?t=2118759&page=2)

And
[http://askubuntu.com/questions/48717/how-to-manually-fix-a-partition-table](http://askubuntu.com/questions/48717/how-to-manually-fix-a-partition-table)

---

### Post by mpgarate on 2013-02-26
I was able to solve this issue with Boot-Repair using the recommended settings. What a great program!
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

This is my output:
[http://paste.ubuntu.com/5566863/](http://paste.ubuntu.com/5566863/)

---

