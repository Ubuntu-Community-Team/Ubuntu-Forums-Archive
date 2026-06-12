---
title: "Is my RAID 5 setup salvageable?"
date: 2016-06-05
forum: General Help
---

### Post by Chesties on 2016-06-05
Hello community,

Looking for some help with my RAID 5 setup. A little bit of background:

Used mdadm to create a RAID 5 using 3 disks, 2TB in size for each disk. I believe one of my disks went bad. The array continued to work in degraded mode. Then I had a power failure taking my machine/server offline. Now, my RAID 5 array only sees 1 active disk. From what I can tell, one disk for sure is no good (sda1). This disk is not part of the array in that it is simply offline. One disk is online, but has a few bad sectors and is not seen as part of the array (sdc1). The third and final disk is online, healthy and seems to be the one that is still actively part of the array (sdb1). I guess the question I have is, is my array salvageable? If yes, any help on how i can get my array operating again would be great. For sure i will need a new disk to replace the bad one, but before i go any further, I just need to know if it is possible to save at this point. Thanks for your feedback in advance!

Here is some information on the current state of my array:

cat /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdb1[1]
      1953382400 blocks super 1.2
      
unused devices: <none>
```

sudo mdadm --detail /dev/md0
```
/dev/md0:
        Version : 1.2
  Creation Time : Thu Jul 25 15:12:48 2013
     Raid Level : raid5
  Used Dev Size : 1953381888 (1862.89 GiB 2000.26 GB)
   Raid Devices : 3
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Fri Nov 20 07:46:42 2015
          State : active, FAILED, Not Started
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : server1:0  (local to host server1)
           UUID : eb865610:64f74d3c:6a663c47:f5195d77
         Events : 1506

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed

```

sudo mdadm --examine /dev/sda1
```
mdadm: cannot open /dev/sda1: No such file or directory
```

sudo mdadm --examine /dev/sdb1
```
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : eb865610:64f74d3c:6a663c47:f5195d77
           Name : server1:0  (local to host server1)
  Creation Time : Thu Jul 25 15:12:48 2013
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 8feeed8a:7c186672:b339e906:b7e31a82

    Update Time : Fri Nov 20 07:46:42 2015
       Checksum : 6525df44 - correct
         Events : 1506

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : .A. ('A' == active, '.' == missing)
```

sudo mdadm --examine /dev/sdc1
```
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : eb865610:64f74d3c:6a663c47:f5195d77
           Name : server1:0  (local to host server1)
  Creation Time : Thu Jul 25 15:12:48 2013
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : b57b3ba1:177d9fa1:87f5528e:62091b0f

    Update Time : Fri Nov 13 12:54:07 2015
       Checksum : bf0db9da - correct
         Events : 1254

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : .AA ('A' == active, '.' == missing)




```

---

### Post by TheFu on 2016-06-06
Are you certain that the cable to sda isn´t bad or just loose?  Check that first.  Back when I used RAID5, one of the disks had a loose SATA cable every few months.  Eventually, I got a SATA cables that locked in-place and it haven´t had any issues since.  Same external disk array has been working for ... almost a decade.

Have you tried to force mdadm to assemble the array?
```

sudo mdadm --assemble /dev/md0 -v --force
```
Do you monitor the SMART data and look for relocated sectors on each disk?
Do you ¨scrub¨ the array to ensure it is consistent?

RAID never replaces backups, as you know.

---

### Post by Fire_Chief on 2016-06-06
You could try to re-add /dev/sdc1 to the array using the --re-add option. The missing disk will be checked for metadata that confirms it is a member of the array and will attempt to add it back into the array in the same position. If that works, then you can run the array in a degraded state until either the sda drive is replaced or you can get the data off of the array.

See more details on mdadm command options at [http://linux.die.net/man/8/mdadm]("http://linux.die.net/man/8/mdadm")

Cheers!

---

### Post by Chesties on 2016-06-06
@TheFu, @Fire_Chief, thanks so much for taking the time to review my scenario and provide feedback. 

Let me follow up on your suggestions:

Checked for loose SATA cables. Everything seems well intact. What i do notice is a ticking noise from one of the drives on startup of the machine. To me, that is the sound of a bad disk. /dev/sda1 i believe is the culprit. It's a Seagate . . .not sure if that matters, but just wanted to throw that out there.

sudo mdadm --assemble /dev/md0 -v --force
```
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sr0: No medium found
mdadm: no RAID superblock on /dev/sdd5
mdadm: no RAID superblock on /dev/sdd2
mdadm: no RAID superblock on /dev/sdd1
mdadm: no RAID superblock on /dev/sdd
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdb1 is busy - skipping
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/md0 is already in use.

```

I don't explicitly monitor the SMART data, no. I know that 2 of my drives have this ability and i have run some commands using smartctl based on some posts, but not sure what to make of the results. Of the 2 disks that are still online, one seems healthy and the other has "a few bad sectors". 

I don't think i have ever explicitly "scrubbed" the array to make sure it is consistent, no.

You are right, RAID is not a replacement for backups. It just get's difficult trying to "backup" TBs of data :)

sudo mdadm --re-add /dev/sdc1
```
mdadm: /dev/sdc1 does not appear to be an md device

```
Not sure if this feedback helps. Any thoughts moving forward? I definitely appreciate the input!

---

### Post by TheFu on 2016-06-06
Clicking means bad disk of some sort.

Did you ¨stop¨ the array before running those commands?  BTW, the mdadm manpage is fairly useful.
Did you try to ¨run¨ the array in degrade mode, though I don´t see how that can work with 2 disks missing in a RAID5 setup.

Don´t buy low-end seagate drives.  There are lots of studies which show seagate to be much, much, likely to fail than any other cheap HDD.  SAS seagates could be a different thing. I don´t play in that space anymore, so don´t know.  Last time a seagate died on me and was still within the warranty period, I didn´t bother get a replacement. Bought a Hitachi and never looked back.  Look for the BackBlaze quarterly HDD studies for more info.

Looks to me like it is time to cut bait, start fresh with new disks and restore from backups.

If you can´t backup the data, then I don´t see why you have it at all. If it is important enough to RAID, then it is important enough to have much more useful backups.

---

### Post by Chesties on 2016-06-07
Ok, so I stopped the array first and tried the assemble command you suggested and it looks like it has started with 2 devices out of the 3.

sudo mdadm --assemble /dev/md0 -v --force
```
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sr0: No medium found
mdadm: no RAID superblock on /dev/sdd5
mdadm: no RAID superblock on /dev/sdd2
mdadm: no RAID superblock on /dev/sdd1
mdadm: no RAID superblock on /dev/sdd
mdadm: no RAID superblock on /dev/sdc
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 1.
mdadm: forcing event count in /dev/sdc1(2) from 1254 upto 1506
mdadm: clearing FAULTY flag for device 0 in /dev/md0 for /dev/sdc1
mdadm: Marking array /dev/md0 as 'clean'
mdadm: no uptodate device for slot 0 of /dev/md0
mdadm: added /dev/sdc1 to /dev/md0 as 2
mdadm: added /dev/sdb1 to /dev/md0 as 1
mdadm: /dev/md0 has been started with 2 drives (out of 3).
```

I then mounted the array to the original location, and voila! I can see data again! Pumped! I am in the process of backing up critical items. Will look to order a new drive to replace the dead one. I have had good luck with Western Digital, so might go that route.

In summary, my raid 5 array was salvageable. Thanks guys for directing me on this. Greatly appreciated!!

---

### Post by Fire_Chief on 2016-06-07
Excellent! Great to hear it is recoverable. If you're good to go, please don't forget to mark the thread (change the title) with the [SOLVED] prefix.

Cheers!

---

