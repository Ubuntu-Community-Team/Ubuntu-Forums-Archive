---
title: "A little confusion about wiping the hard disk"
date: 2014-11-23
forum: General Help
---

### Post by cbiweb on 2014-11-23
Disregard... I was reading the screen wrong..... :\

---

### Post by grahammechanical on 2014-11-23
sd = sata disk. 
sda = first sata disk (even if it is the only hard disk in the machine). Other sata disks are labelled b, c, d and onwards
sda1 = first partition on the first sata disk.
sda2 = second partition on the first, maybe only, hard disk.
sda5 = fifth partition on the first, maybe only, hard disk.

On BIOS machines we are only allowed 4 primary partitions. To work around this problem we make one of the permitted 4 primary partitions into an Extended partition. And in that Extended partition we can create as many Logical partitions as we need.

sda5 = Logical partition inside the Extended partition sda2.

LVM = Logical Volume Manager.

[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

[http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29)

If you want to install another OS on sda then just allow the installer to use the entire disk. Formatting the entire disk is another way to make the existing OS unusable and the data on the drive extremely difficult to access. Deleting the partition table will do the same thing, I understand.

Regards.

---

