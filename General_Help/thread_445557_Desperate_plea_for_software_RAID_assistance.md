---
title: "Desperate plea for software RAID assistance"
date: 2007-05-16
forum: General Help
---

### Post by ktulu1115 on 2007-05-16
i'd really appreciate any advice provided...    I'm in a pretty bad spot here as 2 of the SATA controllers on my server motherboard both simultaneously timed out and my RAID 5 array lost 2 of the 4 drives.  After a reboot, the drives themselves came up fine, the hardware seems to work fine but the array was damaged.

My attempts to restore the array:

```
root@rigel:~# mdadm --add /dev/md0 /dev/sda1
mdadm: cannot get array info for /dev/md0
root@rigel:~# mdadm --add /dev/md0 /dev/sdd1
mdadm: cannot get array info for /dev/md0
root@rigel:~# mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.
root@rigel:~# mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7e23e6f5:e4b60b3f:d570749f:06269f3d
  Creation Time : Sat Dec 23 13:26:02 2006
     Raid Level : raid5
    Device Size : 312568576 (298.09 GiB 320.07 GB)
     Array Size : 937705728 (894.27 GiB 960.21 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed May 16 00:40:06 2007
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 862f9aee - correct
         Events : 0.1628631

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
root@rigel:~# mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7e23e6f5:e4b60b3f:d570749f:06269f3d
  Creation Time : Sat Dec 23 13:26:02 2006
     Raid Level : raid5
    Device Size : 312568576 (298.09 GiB 320.07 GB)
     Array Size : 937705728 (894.27 GiB 960.21 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed May 16 00:40:06 2007
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 862f9b00 - correct
         Events : 0.1628631

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
root@rigel:~# mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7e23e6f5:e4b60b3f:d570749f:06269f3d
  Creation Time : Sat Dec 23 13:26:02 2006
     Raid Level : raid5
    Device Size : 312568576 (298.09 GiB 320.07 GB)
     Array Size : 937705728 (894.27 GiB 960.21 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed May 16 00:42:25 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 86487591 - correct
         Events : 0.1628634

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
root@rigel:~# mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7e23e6f5:e4b60b3f:d570749f:06269f3d
  Creation Time : Sat Dec 23 13:26:02 2006
     Raid Level : raid5
    Device Size : 312568576 (298.09 GiB 320.07 GB)
     Array Size : 937705728 (894.27 GiB 960.21 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed May 16 00:42:25 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 864875a3 - correct
         Events : 0.1628634

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
root@rigel:~# mdadm --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/
sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: Cannot open /dev/sda1: Device or resource busy
mdadm: Cannot open /dev/sdb1: Device or resource busy
mdadm: Cannot open /dev/sdc1: Device or resource busy
mdadm: Cannot open /dev/sdd1: Device or resource busy
mdadm: create aborted
root@rigel:~# 

```

I'm out of ideas as this point.  I found an application called TestDisk that supposedly can recover data from Linux software RAID partitions but I can't seem to get it to recognize the 4 disks as all part of the array, it only allows me to work on one drive at a time.  I'm pretty desperate here as I lost 500+ gigs of data and restoring it would take years.  Any and all suggestions are appreciated.  Thank you.

Regards,
ktulu1115

---

### Post by ayenack on 2007-05-16
That's a KILLER. Try this [link]("http://www.filetransit.com/view.php?id=34088") Also try typing Data Recovery in Synaptic it brings up quite a few recovery tools. I take it you've done all the obvious things like checking cables are connected properly etc. What File System are you using?

Don't know if this will help but try this [link]("http://sysresccd.org/Main_Page") may be what you need.

Good luck. ayenack.

---

### Post by ktulu1115 on 2007-05-16
It's an XFS partition.  The problem isn't with the cables or anything, I'm almost 100% positive its the motherboard.  What's really gets me is that the drives didn't even fail or crash, they just timed out.  All the data that is needed to run the array should be there and intact, I just can't figure out a way to get it working.

I took a look at those links and unfortunately my problem seems somewhat unique and those tools won't be of any assistance.  I appreciate the help, but does anyone else have any further suggestions?  I'm really curious why it said device or resource busy when attempting to re-create the array.

---

### Post by ktulu1115 on 2007-05-16
Oh thank God, I got it working!  I'm posting, hoping this might help some other poor soul in distress.

What I had to do was first stop the array:
root@rigel:~# mdadm --stop /dev/md0

THEN, it allowed me to recreate the array:
```
root@rigel:~# mdadm --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64k
mdadm: /dev/sda1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Sat Dec 23 13:26:02 2006
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Sat Dec 23 13:26:02 2006
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Sat Dec 23 13:26:02 2006
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Sat Dec 23 13:26:02 2006
mdadm: size set to 312568576k
Continue creating array? y
[   455.455135] raid5: raid level 5 set md0 active with 3 out of 4 devices, algorithm 2
mdadm: array /dev/md0 started
```

I mounted the array and verified all was OK.  I'm so happy! :)  Going to ensure the array is rebuilt successfully then, either RMA'ing this motherboard or getting a SATA controller from NewEgg.

---

### Post by ayenack on 2007-05-16
That's such good news mate. I know what's it's like to loose data (not nice).  So all you had to do was rebuild the array how cool is that!!

Well best of luck and heaven help those with raid configs.

ayenack.

---

### Post by radams58 on 2008-02-21
Ok, I have a similar issue, but I'm not entirely sure of the cause...
it appears that ONE of my drives is, definitely, bad
I cannot understand why the **** the other was removed.

I attempted the recreate, but it just chuckled at the bad drive.

```

-----------------------------------------------------
Examine Status 
-----------------------------------------------------
/dev/sda:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : be6d213e:3c1e4184:05d36ab3:de598593 (local to host samba)
  Creation Time : Tue Dec 11 22:32:52 2007
     Raid Level : raid5
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
     Array Size : 1953545984 (1863.05 GiB 2000.43 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Feb 21 05:37:59 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 341d987e - correct
         Events : 0.3350

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8        0        4      active sync   /dev/sda

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       64        2      active sync   /dev/sde
   3     3       8       48        3      active sync   /dev/sdd
   4     4       8        0        4      active sync   /dev/sda
/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : be6d213e:3c1e4184:05d36ab3:de598593 (local to host samba)
  Creation Time : Tue Dec 11 22:32:52 2007
     Raid Level : raid5
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
     Array Size : 1953545984 (1863.05 GiB 2000.43 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Feb 21 03:31:46 2008
          State : active
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 341d6daf - correct
         Events : 0.3331

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       16        1      active sync   /dev/sdb

   0     0       8       32        0      active sync   /dev/sdc
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       64        2      active sync   /dev/sde
   3     3       8       48        3      active sync   /dev/sdd
   4     4       8        0        4      active sync   /dev/sda
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : be6d213e:3c1e4184:05d36ab3:de598593 (local to host samba)
  Creation Time : Tue Dec 11 22:32:52 2007
     Raid Level : raid5
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
     Array Size : 1953545984 (1863.05 GiB 2000.43 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Feb 21 03:31:46 2008
          State : active
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 341d6dbd - correct
         Events : 0.3331

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       32        0      active sync   /dev/sdc

   0     0       8       32        0      active sync   /dev/sdc
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       64        2      active sync   /dev/sde
   3     3       8       48        3      active sync   /dev/sdd
   4     4       8        0        4      active sync   /dev/sda
/dev/sdd:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : be6d213e:3c1e4184:05d36ab3:de598593 (local to host samba)
  Creation Time : Tue Dec 11 22:32:52 2007
     Raid Level : raid5
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
     Array Size : 1953545984 (1863.05 GiB 2000.43 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Feb 21 05:37:59 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 341d98ba - correct
         Events : 0.3350

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       64        2      active sync   /dev/sde

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       64        2      active sync   /dev/sde
   3     3       8       48        3      active sync   /dev/sdd
   4     4       8        0        4      active sync   /dev/sda
/dev/sde:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : be6d213e:3c1e4184:05d36ab3:de598593 (local to host samba)
  Creation Time : Tue Dec 11 22:32:52 2007
     Raid Level : raid5
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
     Array Size : 1953545984 (1863.05 GiB 2000.43 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Feb 21 05:37:59 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 341d98ac - correct
         Events : 0.3350

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       48        3      active sync   /dev/sdd

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       64        2      active sync   /dev/sde
   3     3       8       48        3      active sync   /dev/sdd
   4     4       8        0        4      active sync   /dev/sda
   
-----------------------------------------------------
cat /proc/mdstat
-----------------------------------------------------
   
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd[2](S) sda[4](S) sde[3](S) sdb[1](S) sdc[0](S)
      2441932480 blocks
       
unused devices: <none>


-----------------------------------------------------
Rebuild Attempt 1
-----------------------------------------------------
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=5 /dev/sdc /dev/sdb/ /dev/sde /dev/sdd /dev/sda

mdadm --create --verbose /dev/md0 --level=5 --raid-devices=5 /dev/sdc /dev/sdb/ /dev/sde /dev/sdd /dev/sda
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: /dev/sdc appears to contain an ext2fs file system
    size=1953545984K  mtime=Sun Feb 17 23:08:15 2008
mdadm: /dev/sdc appears to be part of a raid array:
    level=raid5 devices=5 ctime=Tue Dec 11 22:32:52 2007
mdadm: Cannot open /dev/sdb/: Not a directory
mdadm: /dev/sde appears to be part of a raid array:
    level=raid5 devices=5 ctime=Tue Dec 11 22:32:52 2007
mdadm: /dev/sdd appears to be part of a raid array:
    level=raid5 devices=5 ctime=Tue Dec 11 22:32:52 2007
mdadm: /dev/sda appears to contain an ext2fs file system
    size=1261485828K  mtime=Fri Feb  8 10:31:11 1974
mdadm: /dev/sda appears to be part of a raid array:
    level=raid5 devices=5 ctime=Tue Dec 11 22:32:52 2007
mdadm: create aborted

```


HELP!?!

2.0 TB of data milling about on this array.  I'd hate to lose it!

---

### Post by fjgaude on 2008-02-21
Gosh, interesting, radams58. Two things, the "/" marks after some of the drive names and not others?

And the drives are not partitions? No, sda1, sdb1, etc?

What does mdadm -D /dev/md0 show?

---

### Post by radams58 on 2008-02-22
1 Because I'm a lazy typist apparently
2 Nope whole drive, I thought thats the way things were done
3
```

        Version : 00.90.03
  Creation Time : Thu Feb 21 10:41:31 2008
     Raid Level : raid5
     Array Size : 1953545984 (1863.05 GiB 2000.43 GB)
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Feb 22 12:29:37 2008
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : b4c1bbd8:eb21657d:05d36ab3:de598593 (local to host samba)
         Events : 0.10

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       16        1      active sync   /dev/sdb
       2       8       64        2      active sync   /dev/sde
       3       8       48        3      active sync   /dev/sdd
       4       8        0        4      active sync   /dev/sda

```

---

### Post by wirelessmonkey on 2008-02-22
FWIW, I had so many problems with a 5TB Raid5 array in Ubuntu, I wasted months trying to keep things working.  For that storage server, I switched to openSUSE 10.3, which has an integrated and very intelligent software raid management utility, and haven't had a problem since.

---

### Post by radams58 on 2008-02-22
I'm willing to switch, I'm willing to spend STUPID amounts of time and money to get my data back...
I JUST WANT IT BACk!!

```

[   75.730000] EXT2-fs error (device md0): ext2_check_descriptors: Block bitmap for group 3968 not in group (block 197132288)!
[   75.730000] EXT2-fs: group descriptors corrupted!
[ 4504.650000] EXT2-fs error (device md0): ext2_check_descriptors: Block bitmap for group 3968 not in group (block 197132288)!
[ 4504.650000] EXT2-fs: group descriptors corrupted!

```

It seems like maybe it's back up?

---

