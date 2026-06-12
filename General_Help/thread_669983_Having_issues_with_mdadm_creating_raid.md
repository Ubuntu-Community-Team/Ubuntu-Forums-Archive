---
title: "Having issues with mdadm creating raid"
date: 2008-01-16
forum: General Help
---

### Post by Cr0n_J0b on 2008-01-16
I'm trying to build a simple Raid 5 array out of 4 SATA drives.  They dries are , 250GB, 250GB, 500GB and 500GB.  I've created partitions on each of them that are the exact same size, roughly 250GB.

/dev/sda1, /dev/sdb1. /dev/sdc1, /dev/sdd1

I created an array on these partiions before, but after a power outage it just died.  not sure why...but since there was little of value on there, I just decided to rebuild the set from scratch.  I first tried...

mdadm --create /dev/md0 --level=5 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1

The device would start and then begin rebuilding as normal...about 5 minutes later it would show up like this.

+++++++++++++++++++++++++++++++++++++++
        Version : 00.90.03
  Creation Time : Wed Jan 16 21:03:10 2008
     Raid Level : raid5
     Array Size : 732563712 (698.63 GiB 750.15 GB)
  Used Dev Size : 244187904 (232.88 GiB 250.05 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jan 16 21:05:22 2008
          State : clean, degraded
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 26ab635c:6dcc91db:645e3c10:269b8dbf
         Events : 0.34

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed
       3       0        0        3      removed

       4       8       49        -      spare   /dev/sdd1
       5       8        1        -      faulty spare   /dev/sda1

+++++++++++++++++++++++++++++++++++++
So it looks like 2 drives are faulty...but I can't see that they are.  I have tested both of the drives and they appear fine.  I can mount them and use them as individual drives, but in the raid set it's not working.

I tried zeroing the superblocks on each and I've repartitioned each of the drives.  still the same result.

any help is appreciated.

---

### Post by fjgaude on 2008-01-17
Well, I think it is because mdadm thinks those drives were in another array, and as you know they were.

So you just zero the superblocks of the two drives and start over:

```
sudo mdadm --zero-superblock/ /dev/sd[n1]
```

Also, two sites help in understanding software raid as used by Ubuntu:

[http://www.networknewz.com/2003/0113.html](http://www.networknewz.com/2003/0113.html)

Helpful to do searches and with a Table of Contents:

[http://man-wiki.net/index.php/8:mdadm](http://man-wiki.net/index.php/8:mdadm)

Let us know how you do.

---

### Post by Cr0n_J0b on 2008-01-17
Thanks for the reply.  As I mentioned in the original note, I have already zeroed out the superblocks for each of the drives.  One thing that i noticed that after doing this, I still got the error message saying that two of the drives looked like they were in an existing array, so I did it again, with the same results.  It feels like the superblocks, just aren't getting overwritten on these two drives.  I have since built them into a RAID 0 array with absolutely no issues.  That's what's strange, I can put them in a RAID 0 array, but when I go to put them back into a RAID 5 array, I get the same results.

Any help is appreciated.

---

### Post by fjgaude on 2008-01-17
I can't help beyond what is available in the man pages... try -fail and -remove, things like that.

---

