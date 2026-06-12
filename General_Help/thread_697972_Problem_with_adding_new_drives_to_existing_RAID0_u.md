---
title: "Problem with adding new drives to existing RAID0 using mdadm"
date: 2008-02-15
forum: General Help
---

### Post by hansonlee on 2008-02-15
I built a old software RAID0 array with two 180 GB drives using mdadm. Recently, it is full so I bought two additional 500GB SATA drives trying to expand it. The new drives installed fine and I created a primary partition on each of them (sda1, sdb1). Here's what they look like under fdisk:

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux



Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux


```

My existing raid0 array looks like this using mdadm:

```

/dev/md0:
        Version : 00.90.01
  Creation Time : Mon Dec  5 17:17:54 2005
     Raid Level : raid0
     Array Size : 380202112 (362.59 GiB 389.33 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Dec  5 17:17:55 2005
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 70ac061b:6cb5c31d:87494d5b:144cfb60
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       3        3        0      active sync   /dev/hda3
       1       3       65        1      active sync   /dev/hdb1

```

However, when I want to add new drives to the existing array, I got this error message:

```


hanson@lsa-271c-004:~$ sudo mdadm /dev/md0 -a /dev/sda1
mdadm: hot add failed for /dev/sda1: Invalid argument

hanson@lsa-271c-004:~$ sudo mdadm /dev/md0 -a /dev/sdb1
mdadm: hot add failed for /dev/sdb1: Invalid argument


```

Unmount the array does not solve the problem. Also Ubuntu and swap are installed on separated partitions. As seen in /etc/fstab

```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/md0        /mnt/raid-array ext2    defaults        0       0


```

By the way, I am still using the old 5.04, and yet to find a way to upgrade....

I looked at many posts but I can't find the exact answer and I am not really an expert in Linux.

Anyone has an idea? Thanks.

---

### Post by hansonlee on 2008-02-23
OK I've answered my own question

Apparently, you can't add new drives to Raid0 array. This can only be done in Raid1/4/5.

For those configurations, although it is possible to use drives/partitions with unequal capacities, the actual capacity is determined by the smallest drives/partitions.

So this is what I've done:

My computer has two 200GB drives, and I add two 500gb drives.

One of the 200gb drive is partitioned into three parts: the main partition where OS resides, the swap and a raid partition which, together with the second 200gb drive, forms a raid0 array.

Since my Ubuntu is too old (5.04), I first copy everything to one of the new 500gb drives, format the rest, and install Ubuntu 7.10.

To decrease amount of waste spaces, each 200gb drive is partitioned into a 34gb part and a 166gb part. The unused 500gb drive is divided into three 166gb partitions.  One of the 34 gb part is used for OS, and the other is used for tmp. A small partition (2G) is used for swap. All the 166gb partitions (5 total) are combined to form a raid5 array.

I then copy the stuff back to the raid array and the OS, format the 2nd 500gb drive, and again divide into three 166gb partitions.

Using this [mdadm function]("http://scotgate.org/?p=107"), the three additional 166gb partitions are added back to the existing raid5 array.

In the future, as long as new drives are partitioned into 166gb ones, they can be added to the array without wasting space. Of course, this undermines the redundancy of disk arrays, but that's the price I pay for using drives with unequal capacities....:)

---

