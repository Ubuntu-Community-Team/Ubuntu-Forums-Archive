---
title: "need help saving my RAID5 array"
date: 2007-10-23
forum: General Help
---

### Post by IndieRockSteve on 2007-10-23
I was previously running another Debian based distro when I tried to add two drives to my array which would make it 2.5TB, but I don't believe the kernel had large device support because it stalled at around 80%.  So I decided to install Gutsy and hopefully finish reshaping/rebuilding the array.

So I've got array partitions on:
/dev/sda1
/dev/sdb1
/dev/sdc1
/dev/sdd1
/dev/sde
/dev/sdf

(yes, sde and sdf are not at sde1 and sdf1, something that I don't know how I did but would like to "fix" if possible as well.)

an mdadm --examine shows:
> 
# mdadm -E /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde /dev/sdf
/dev/sda1:
          Magic : a92b4efc
        Version : 00.91.03
           UUID : edda27c6:48dbf86f:197c726b:c481dd54
  Creation Time : Thu Apr  5 15:15:23 2007
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 2441919680 (2328.80 GiB 2500.53 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

  Reshape pos'n : 2147469440 (2047.99 GiB 2199.01 GB)
  Delta Devices : 1 (5->6)

    Update Time : Mon Oct 22 07:35:18 2007
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 6840ee86 - correct
         Events : 0.610424

         Layout : left-symmetric
     Chunk Size : 32K

      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1

   0     0       8       65        0      active sync
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       81        3      active sync
   4     4       8        1        4      active sync   /dev/sda1
   5     5       8       17        5      active sync   /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.91.03
           UUID : edda27c6:48dbf86f:197c726b:c481dd54
  Creation Time : Thu Apr  5 15:15:23 2007
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 2441919680 (2328.80 GiB 2500.53 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

  Reshape pos'n : 2147469440 (2047.99 GiB 2199.01 GB)
  Delta Devices : 1 (5->6)

    Update Time : Mon Oct 22 07:35:18 2007
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 6840ee94 - correct
         Events : 0.610424

         Layout : left-symmetric
     Chunk Size : 32K

      Number   Major   Minor   RaidDevice State
this     1       8       49        1      active sync   /dev/sdd1

   0     0       8       65        0      active sync
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       81        3      active sync
   4     4       8        1        4      active sync   /dev/sda1
   5     5       8       17        5      active sync   /dev/sdb1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.91.03
           UUID : edda27c6:48dbf86f:197c726b:c481dd54
  Creation Time : Thu Apr  5 15:15:23 2007
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 2441919680 (2328.80 GiB 2500.53 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

  Reshape pos'n : 2147469440 (2047.99 GiB 2199.01 GB)
  Delta Devices : 1 (5->6)

    Update Time : Mon Oct 22 07:35:18 2007
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 6840eea2 - correct
         Events : 0.610424

         Layout : left-symmetric
     Chunk Size : 32K

      Number   Major   Minor   RaidDevice State
this     0       8       65        0      active sync

   0     0       8       65        0      active sync
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       81        3      active sync
   4     4       8        1        4      active sync   /dev/sda1
   5     5       8       17        5      active sync   /dev/sdb1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.91.03
           UUID : edda27c6:48dbf86f:197c726b:c481dd54
  Creation Time : Thu Apr  5 15:15:23 2007
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 2441919680 (2328.80 GiB 2500.53 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

  Reshape pos'n : 2147469440 (2047.99 GiB 2199.01 GB)
  Delta Devices : 1 (5->6)

    Update Time : Mon Oct 22 07:35:18 2007
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 6840eeb8 - correct
         Events : 0.610424

         Layout : left-symmetric
     Chunk Size : 32K

      Number   Major   Minor   RaidDevice State
this     3       8       81        3      active sync

   0     0       8       65        0      active sync
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       81        3      active sync
   4     4       8        1        4      active sync   /dev/sda1
   5     5       8       17        5      active sync   /dev/sdb1
/dev/sde:
          Magic : a92b4efc
        Version : 00.90.03
           UUID : edda27c6:48dbf86f:197c726b:c481dd54
  Creation Time : Thu Apr  5 15:15:23 2007
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 5
Preferred Minor : 0

    Update Time : Fri Oct 19 23:17:03 2007
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1
       Checksum : 682b24a9 - correct
         Events : 0.30

         Layout : left-symmetric
     Chunk Size : 32K

      Number   Major   Minor   RaidDevice State
this     4       8        0        4      spare   /dev/sda

   0     0       8       65        0      active sync
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       81        3      active sync
   4     4       8        0        4      spare   /dev/sda
/dev/sdf:
          Magic : a92b4efc
        Version : 00.90.03
           UUID : edda27c6:48dbf86f:197c726b:c481dd54
  Creation Time : Thu Apr  5 15:15:23 2007
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1953535744 (1863.04 GiB 2000.42 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Sun Oct 21 21:29:01 2007
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 683797d5 - correct
         Events : 0.324804

         Layout : left-symmetric
     Chunk Size : 32K

      Number   Major   Minor   RaidDevice State
this     5       8       16       -1      spare   /dev/sdb

   0     0       8       65        0      active sync
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       81        3      active sync
   4     4       8        1        4      active sync   /dev/sda1


and what I'm going for is a 6 drive RAID5 array with no spares.

all the UUID's match but it looks like mdadm gets hickup'd with the /dev/sde and /dev/sdf partitions:
> 
# mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde
mdadm: superblock on /dev/sde doesn't match others - assembly aborted
root@mythcenter:/etc/mdadm# mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde /dev/sdf
mdadm: superblock on /dev/sde doesn't match others - assembly aborted
root@mythcenter:/etc/mdadm# mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sdf /dev/sde
mdadm: superblock on /dev/sdf doesn't match others - assembly aborted
root@mythcenter:/etc/mdadm#


somehow they all worked with the previous install I had, and I'm hoping to get them working again. I figure if I can at least get it assembled and built with the sde/sdf issue I can then format that partition and have it rebuild it on sde1/sdf1 like they should be. hours and hours of rebuilding, but oh well!

so yea, any help in this regard is much appreciated! thanks!!

---

### Post by fjgaude on 2007-10-23
Is /dev/sde and /dev/sdf really not partitions, i.e., /dev/sd[ef]1

Try assemble md0 without them and then add them back, after you make sure they are formatted to sde1 and sdf1... you have to have a filesystem on them. Use Gnome or whatever is handy.

---

### Post by IndieRockSteve on 2007-10-23
well, i tried that, but it didn't work, sde and sdf were already "part of" the array from the previous grow attempt.

sad side is, i was able to get the array to come together but after it finished reshaping both jfs superblocks were corrupt.

so I'm starting over... sadly... my luck.

anyway, now i need to build a new array but i can't get the dev system to recognize the partitions on sde and sdf so while cfdisk shows a sde1 and sdf1 there is no /dev/sde1 or /dev/sdf1

anyone know how to solve this?

---

### Post by fjgaude on 2007-10-24
Well, you need to stop the array, then remove each drive from the array. mdadm permits this to happen with its various commands. The problem is the drives have the tags within them even if you create a new filesystem for them.

```
sudo mdadm --stop /dev/md0

sudo mdadm --manage --set-faulty /dev/md32 /dev/sda1
```

Like that.

---

### Post by IndieRockSteve on 2007-10-24
so in my case to fix the sde and sdf issue I'd have to do

mdadm --manage --set-faulty /dev/md32 /dev/sde

then what would I do to get it to use /dev/sde1 instead?

(then after that rebuilds I assume I could do the same for /dev/sdf ?)

thanks!

---

### Post by fjgaude on 2007-10-24
You would format the sde drive to have a partition: /dev/sde1 using cfdisk. That /dev/md32 was just an example; use your md[n] value.

---

### Post by IndieRockSteve on 2007-10-24
got it, so the set-faulty option basically takes it out of the array which after I can re-create the partition and then add it back to the array.

thanks!

---

### Post by fjgaude on 2007-10-24
That's the ticket to ride... what we need is a booklet that fully covers all the aspect of mdadm, one that has more examples than the man pages.

Good luck.

---

