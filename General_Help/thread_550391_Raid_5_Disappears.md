---
title: "Raid 5 Disappears"
date: 2007-09-13
forum: General Help
---

### Post by pnotequalsnp on 2007-09-13
I have (*ahem had) a raid 5 setup with four 500GB SATA hard drives for storage.  I rebooted the machine and it did not mount the raid drive.  

Short Version: mdstat says I only have 2/4 working drives, but it looks like I have 3/4 (at least) working drives.

Long Version:
So I checked mdastat
 ```
 
>sudo cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] 
md0 : inactive sdc1[1](S) sdd1[2](S)
      976767872 blocks
       
unused devices: <none>

```
and that was odd so I tried to use mdadm
```

>sudo mdadm -As /dev/md0
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.

```
Then I thought that 2(!) drives out of the 4 failed, no way since I just bought them and it is been working for about 4 days now.  So then I used sfdisk for each of the four drives
```

>sudo sfdisk -l /dev/sdb

Disk /dev/sdb: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0       -       0          0    0  Empty
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty

>sudo sfdisk -l /dev/sdc

Disk /dev/sdc: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdc1          0+  60800   60801- 488384001   83  Linux
/dev/sdc2          0       -       0          0    0  Empty
/dev/sdc3          0       -       0          0    0  Empty
/dev/sdc4          0       -       0          0    0  Empty

>sudo sfdisk -l /dev/sdd

Disk /dev/sdd: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdd1          0+  60800   60801- 488384001   83  Linux
/dev/sdd2          0       -       0          0    0  Empty
/dev/sdd3          0       -       0          0    0  Empty
/dev/sdd4          0       -       0          0    0  Empty

>sudo sfdisk -l /dev/sde

Disk /dev/sde: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sde1          0+  60800   60801- 488384001   83  Linux
/dev/sde2          0       -       0          0    0  Empty
/dev/sde3          0       -       0          0    0  Empty
/dev/sde4          0       -       0          0    0  Empty


```
and we see that there is something wrong with /dev/sdb (where did you go?).

But when I try to start up the device (because it looks like I have 3 working) I get the same error that there are only 2 drives available.

So then I tried to use mdadm again and got:
```

>sudo mdadm -E /dev/sdb1
mdadm: cannot open /dev/sdb1: No such file or directory
nhomer@ubuntu-desktop:~$ sudo mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a5dcb6ff:0d931c7f:bb855af7:201184b4 (local to host ubuntu-desktop)
  Creation Time : Sun Sep  9 22:14:31 2007
     Raid Level : raid5
    Device Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Thu Sep 13 01:43:04 2007
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : e31dd26f - correct
         Events : 0.28452

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1

>sudo mdadm -E /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a5dcb6ff:0d931c7f:bb855af7:201184b4 (local to host ubuntu-desktop)
  Creation Time : Sun Sep  9 22:14:31 2007
     Raid Level : raid5
    Device Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Thu Sep 13 01:43:04 2007
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : e31dd281 - correct
         Events : 0.28452

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       49        2      active sync   /dev/sdd1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1

>sudo mdadm -E /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a5dcb6ff:0d931c7f:4bc81c71:77d10fa7
  Creation Time : Sun Sep  9 22:14:31 2007
     Raid Level : raid5
    Device Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Thu Sep 13 01:43:04 2007
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : cb201f00 - correct
         Events : 0.28452

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       65        3      active sync   /dev/sde1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1

```

Basically at this point I am open to any suggestions (I don't want to have to reload ~1 TB of data please).  How do I get this working and am I even on the right track?

-------------------------------------------------

I really appreciate all the help on UbuntuForums.org

---

### Post by fjgaude on 2007-09-13
What does sudo fdisk -l show?

And also sudo mdadm -D /dev/md0 ?

frank

---

### Post by pnotequalsnp on 2007-09-13
Here is sudo fdisk -l (note that I have my OS' on sda):
```

sudo fdisk -l

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        9962    39062047+  83  Linux
/dev/sda3            9963       10084      979965   82  Linux swap / Solaris
/dev/sda4           10085       18241    65521102+   b  W95 FAT32

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   83  Linux

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001   83  Linux

```
and here is sudo mdadm -D /dev/md0:
```

sudo mdadm -D /dev/md0
mdadm: md device /dev/md0 does not appear to be active.

```

---

### Post by pnotequalsnp on 2007-09-14
Ok, here's how I fixed the problem (refer to[ http://ubuntuforums.org/showthread.php?t=410136]("http://ubuntuforums.org/showthread.php?t=410136") for more).  

I saw that the first drive (/dev/sdb1) was no more, since the partition tables were gone.  Theoretically I have 3/4 left so I can rebuild.  The problem was that the uuid on the last drive (/dev/sde) was not matching the second and the third (/dev/sdc and /dev/sdd).  So I changed the uuid by ignoring it and rebuilding the array using disks 2, 3 and 4
```

sudo mdadm --create /dev/md0 --assume-clean --level=5 --raid-devices=4 missing /dev/sdc1 /dev/sdd1 /dev/sde1

```
That fixed the uuid on the fourth drive and got the array running.  I reformatted /dev/sdb1 (using gparted) and added it back to the array:
```

sudo mdadm /dev/md0 --add /dev/sdb1

```

Be careful about the order in which you specify the arrays.  I hope this experience is useful to someone else!

---

### Post by fjgaude on 2007-09-14
Wonderful, and thanks... we all learn something as we get into trouble. It is neat that you fixed this... I'm sure I'll have this problem one of these days... I'll remember you and you fix. Thanks again.

frank

---

### Post by Exarch on 2007-12-27
I had a similar issue with my raid 5 that was fixed like this.

It was built from /dev/sdb1, /dev/sdc1, and /dev/sdd1

mdadm -E /dev/sdb1 displayed a status where sdb1 itself was fine, but the other two drives broken. Doing a mdadm --run gave me an error that only one valid drive was found and that it wasn't enough to rebuild the array.

But when I did the -E on sdc1 and sdd1, all three drives displayed as fine. So I guess some index table on sdb1 or whatever mdadm uses broke which caused the buggy display.

Recreating the array with the above command and putting sdb1 as missing made the array work again and I could re-add the sdb1 as a new spare and recover the array back onto three drives.

---

