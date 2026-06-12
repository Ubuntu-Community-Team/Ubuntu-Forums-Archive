---
title: "please help my raid"
date: 2007-12-21
forum: General Help
---

### Post by tgpfarm on 2007-12-21
ok i will try to give a much info as i can.  I created a 3 disk raid5

i used this tutorial:
[http://www.gagme.com/greg/linux/raid-lvm.php](http://www.gagme.com/greg/linux/raid-lvm.php)

the devices are:
/dev/sdb1
/dev/sdc1
/dev/sdd1

the array is:
/dev/md0

i created a lvm on top of the raid like this:
pvcreate /dev/md0
vgcreate -s 32M lvm-raid /dev/md0

At this point everything was fine.  I transfered some files to the array, tested the speed of copying files and what not.

Before i actually started to use the array i wanted to simulate a drive failure and recover from it, to make sure it works like it is suppose to.

so i did the command:
/sbin/mdadm /dev/md0 -f /dev/sdc1

so now it looks like this:
```
mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Fri Dec 21 04:58:00 2007
     Raid Level : raid5
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
    Device Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Dec 21 11:41:10 2007
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : b64371b3:8e595c90:cf6b357c:9d27c08c
         Events : 0.46

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed
       2       8       49        2      active sync   /dev/sdd1

```

now the tutorial say to do:
/sbin/mdadm /dev/md0 -a /dev/sdc1

which gives me this error:
```
mdadm /dev/md0 -a /dev/sdc1
mdadm: Cannot open /dev/sdc1: Device or resource busy

```

other commands i have tried with no success:
mdadm --add /dev/md0 /dev/sdc1
mdadm --manage /dev/md0 --re-add /dev/sdc1

also something i don't know if its worth noting or not:
```
mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : b64371b3:8e595c90:cf6b357c:9d27c08c
  Creation Time : Fri Dec 21 04:58:00 2007
     Raid Level : raid5
    Device Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Dec 21 08:21:00 2007
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 64f8625 - correct
         Events : 0.2

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1

```

---

### Post by tgpfarm on 2007-12-21
let me know if you need more info.

---

### Post by fjgaude on 2007-12-22
You might try a remove for the drive then add it back:

```
/sbin/mdadm /dev/md0 -r /dev/sdc1
```

```
/sbin/mdadm /dev/md0 -a /dev/sdc1
```

I think I had to do that once to get a drive back into its original array.

---

### Post by tgpfarm on 2007-12-22
thanks for the post, but from this:
```
mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Fri Dec 21 04:58:00 2007
     Raid Level : raid5
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
    Device Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Dec 21 11:41:10 2007
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : b64371b3:8e595c90:cf6b357c:9d27c08c
         Events : 0.46

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed
       2       8       49        2      active sync   /dev/sdd1
```

its already been removed
And when i try to do it again i get this:
```
/sbin/mdadm /dev/md0 -r /dev/sdc1
mdadm: hot remove failed for /dev/sdc1: No such device or address
```

P.S. Is there a better raid tool out there for software raid?
Since i haven't started actually using this array, I could just rebuild it  using better software.

---

### Post by fjgaude on 2007-12-22
I don't know of anything better than mdadm... I've never had any troubles like you are having.

The last thing you could try is reformating the sdc drive and then try adding it to your present array. You should be able to add a drive to any raid5 array with mdadm.

I wish I could be of more help. From what I know, mdadm is solid and used by lots of folks.

---

