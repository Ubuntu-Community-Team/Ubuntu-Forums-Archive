---
title: "Partitioning USB Drive"
date: 2016-01-16
forum: General Help
---

### Post by WinterMadness on 2016-01-16
This is a separate issue than my other thread.

Running: 
```

sudo fdisk -l
```
gives


Disk /dev/sdb: 29.8 GiB, 32010928128 bytes, 62521344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x70f56db4

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *        0  3801087  3801088  1.8G  0 Empty
/dev/sdb2        2048 62521343 62519296 29.8G ef EFI (FAT-12/16/32)



I only have one usb drive in... This used to be all on sdb1.  When I open gparted and then goto GParted->Devices I only see /dev/sdb2

how do I make it normal again?

---

### Post by Dennis N on 2016-01-16
Are you sure? My gparted shows only disk designations (sda, sdb, sdc) under **Gparted > Devices**. sda1, sdb2, refer to partitions on a particular disk. 

Use gparted, and **Device > Create Partition Table** will erase the disk partitions and show unallocated space. Any data on the disk will be lost. Then you can create new partitions from that space.

Are you still doing the installer? I also added a post to the other thread.

---

### Post by WinterMadness on 2016-01-16
what format should I use?

---

### Post by sudodus on 2016-01-16
When you flash an iso file to a pendrive with dd (or mkusb), it will 'inherit' the file system of the iso file (that was originally designed for CD or DVD, and modified with isohybrid).

I'm not sure about Manjaro, but Ubuntu's iso files have an ISO 9660 file system, and there are some strange partitions, that are not recognized by all tools. Usually lsblk can identify it

```
sudo lsblk -fm
```

If you want to re-use your pendrive as a data storage device after using it for installing, you can do it via the [wipe menu of mkusb](https://help.ubuntu.com/community/mkusb/wipe).

***Edit:*** the standard format at least for small USB pendrives is an MSDOS partition table and one partition with a FAT32 file system.

---

