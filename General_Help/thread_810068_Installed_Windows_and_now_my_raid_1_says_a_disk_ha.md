---
title: "Installed Windows and now my raid 1 says a disk has failed?"
date: 2008-05-27
forum: General Help
---

### Post by ASULutzy on 2008-05-27
It's possible that my hard disk failed the exact moment I installed Windows Vista, but it seems very unlikely... I'll post some stuff that may help, hopefully someone can give me some direction here because I'm clueless as to what I should even try...
```
buntu@ubuntu:~$ sudo mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 3e9201b8:fbdc6e80:d919d176:d92b132e
  Creation Time : Fri May  2 20:00:38 2008
     Raid Level : raid1
  Used Dev Size : 112414720 (107.21 GiB 115.11 GB)
     Array Size : 112414720 (107.21 GiB 115.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Tue May 27 03:17:06 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 2ce8fa63 - correct
         Events : 0.2766


      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
ubuntu@ubuntu:~$ sudo mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 3e9201b8:fbdc6e80:d919d176:d92b132e
  Creation Time : Fri May  2 20:00:38 2008
     Raid Level : raid1
  Used Dev Size : 112414720 (107.21 GiB 115.11 GB)
     Array Size : 112414720 (107.21 GiB 115.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Wed May 28 02:54:23 2008
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 2cea4707 - correct
         Events : 0.2790


      Number   Major   Minor   RaidDevice State
this     1       8       49        1      active sync   /dev/sdd1

   0     0       0        0        0      removed
   1     1       8       49        1      active sync   /dev/sdd1
ubuntu@ubuntu:~$ cat /proc/mdstat 
Personalities : [raid1] 
md0 : active raid1 sdc1[2](F) sdd1[1]
      112414720 blocks [2/1] [_U]
      
unused devices: <none>
ubuntu@ubuntu:~$ cat /proc/partitions 
major minor  #blocks  name

   8     0   39082680 sda
   8     1   39079936 sda1
   8    16  976762584 sdb
   8    17  976760001 sdb1
   8    32  117220824 sdc
   8    33  112414806 sdc1
   8    34          1 sdc2
   8    37    4803403 sdc5
   8    48  117220824 sdd
   8    49  112414806 sdd1
   8    50          1 sdd2
   8    53    4803403 sdd5
   8    64  488386584 sde
   8    65  488384512 sde1
   8    80    1981952 sdf
   8    81    1467488 sdf1
   8    82     513936 sdf2
   7     0    1345404 loop0
   9     0  112414720 md0
```

Mucho gracias in advance:guitar::lolflag:

edit:Perhaps this command would be useful in finding out what's wrong```
ubuntu@ubuntu:~$ sudo mdadm --query --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Fri May  2 20:00:38 2008
     Raid Level : raid1
     Array Size : 112414720 (107.21 GiB 115.11 GB)
  Used Dev Size : 112414720 (107.21 GiB 115.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed May 28 02:54:23 2008
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0

           UUID : 3e9201b8:fbdc6e80:d919d176:d92b132e
         Events : 0.2790

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       49        1      active sync   /dev/sdd1

       2       8       33        -      faulty spare   /dev/sdc1

```

---

### Post by ASULutzy on 2008-05-28
Well, it looks like the hard drive is bad... That's really shady timing though.

Now I can't seem to get my install to boot from the degraded array... Any ideas?

---

### Post by danwood76 on 2008-05-28
You realise of course that windows will not be able to use the software array.
If windows decided it wanted to write to either of those disks it will cause an issue in your RAID array.

I seriously doubt the drive failed, more like windows decided to screw you.
Try rebuilding the array.

---

### Post by ASULutzy on 2008-05-28
No, I tried rebuilding it, and obviously I didn't try to install Windows to a disk that was a member of the array.

smartctl shows the drive is definitely not happy, and it was being detected incorrectly in the BIOS.

It really looks like the drive is hosed.

But now my problem is that Ubuntu doesn't seem to like to boot from a degraded array. It tries for a little bit and then falls back to a busybox prompt... I think I may be copying over my home folder and then reinstalling... I don't really understand the point of having a RAID-1 if Ubuntu won't boot from a degraded array.

edit: to give a little more detail, I did force it to rebuild and it was going horribly slow, like 3K/s, and it aborted a couple times with all sorts of errors in dmesg about how the drive was fubarred. So yea, any idea how to get my system up and runnning again short of buying another hard disk and adding it to the raid?

---

