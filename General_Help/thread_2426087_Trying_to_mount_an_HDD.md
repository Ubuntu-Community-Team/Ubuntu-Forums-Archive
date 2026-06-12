---
title: "Trying to mount an HDD"
date: 2019-09-04
forum: General Help
---

### Post by tirengarfio2 on 2019-09-04
Hi,

I would like to mount this HDD:

> $ parted -l
Model: ATA ST31500341AS (scsi)
Disk /dev/sda: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  2098MB  2097MB  linux-swap(v1)        raid
 2      2098MB  1500GB  1498GB                        raid

but I'm getting this when trying to mount it:
> 
sudo mount -t auto /dev/sda /media/test
mount: you must specify the filesystem type

---

### Post by TheFu on 2019-09-04
**sda** isn't a partition. You cannot mount an entire drive (well, not really true, just a really, really, really, really, bad idea).

**sda1** is the swap partition, but it has a RAID flag.  You don't mount swap.  You enable it in the fstab.  

**sda2** is marked with a RAID flag.  It needs to be part of a RAID-set, which will create a RAID device - usually something like /dev/md1.  Then you'd create a file system on the RAID device using something like **mkfs -t ext4 /dev/md1**

Lastly, the partition with a file system can be mounted in a number of different ways.
Assuming /media/test directory exists, then **sudo mount /dev/md1 /media/test** will mount it.

If you didn't run 3 or more **mdadm** commands to create the RAID set, then none of that will work.  You'll need to clear the RAID flag, change the partition type using parted, fdisk, gparted or some other partitioning tool.  Then make the file system and mount it.

"ubuntu fstab" - will find a long page with lots of details about modifying the fstab to mount a partition with a file system.

Clear as mud?

---

