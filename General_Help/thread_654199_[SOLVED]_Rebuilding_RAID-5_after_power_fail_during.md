---
title: "[SOLVED] Rebuilding RAID-5 after power fail during grow"
date: 2007-12-30
forum: General Help
---

### Post by karatefish on 2007-12-30
Hi all,

I added another disk to my new RAID-5 array during the setup of my new computer, increasing from 2 disks to 3. The array was being grown onto the new disk, when the power shut off.

Now, the array won't mount on reboot. The output of mdadm query is:```

# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.91.03
  Creation Time : Sat Dec 29 15:37:18 2007
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Dec 30 18:54:50 2007
          State : active, degraded, Not Started
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

  Delta Devices : 1, (2->3)

           UUID : edc7e813:a81d185d:95e159ea:5a1a149d (local to host newtherin)
         Events : 0.129313

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       65        1      active sync   /dev/sde1
       2       0        0        2      removed
```

Checking the md superblock of the disks shows:
```

# mdadm -E /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : edc7e813:a81d185d:95e159ea:5a1a149d (local to host newtherin)
  Creation Time : Sat Dec 29 15:37:18 2007
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

  Reshape pos'n : 388870528 (370.86 GiB 398.20 GB)
  Delta Devices : 1 (2->3)

    Update Time : Sun Dec 30 18:54:50 2007
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 976ac2b - correct
         Events : 0.129313

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1

```

How can I get the array back with the data intact?

I've seen other posts on rebuilding RAID5 arrays, with various solutions:  Stop the array and recreate it,  or re-add the disks. What is the correct method that's not going to bork all my data?

Thanks very much in advance for your help

---

### Post by PilotJLR on 2007-12-30
This array was initially a 2 disk RAID 5???

I know such a setup is possible with linux raid, but keep in mind 3 disks are the required minimum with RAID 5. This means you were basically in a degraded, no fault-tolerance state the whole time.
If I misunderstood the initial condition, please clarify...

If you were 2 disk RAID 5 when the power pulled, then I don't have a solution for you right now, though hopefully someone else will. It is possible the power failure + the degraded initial state is too much to overcome.

But in the future... 3 disk minimum, and buy a UPS. Pay the extra few bucks for an APC Smart UPS, they are great.

---

### Post by karatefish on 2007-12-30
Yeah, I realise that the 2-disk RAID5 is not technically correct, it was a temporary setup while migrating data off the old machine, as I didn't have the funds to create the 3-disk array without reusing a disk. Not terribly smart, I know.

Does anyone have a good knowledge of the way the grow process works? Is it possible to restore it successfully at this point?

What would be the correct procedure if the array had been a 3-disk array growing to 4-disk?

---

### Post by psusi on 2007-12-30
Have you tried asking mdadm to assemble the array by hand and passing it the 3 disks?

---

### Post by karatefish on 2007-12-30
Yes, I tried to assemble the array, but it seems it's already done?```

# mdadm -vv -A /dev/md0 --uuid=edc7e813:a81d185d:95e159ea:5a1a149d
mdadm: device /dev/md0 already active - cannot assemble it

```

Note that /proc/mdstat doesn't seem to agree:```

# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sde1[1]
      488383936 blocks super 0.91

unused devices: <none>

```

Stopping the array and retrying the assembly gets me back to the same point:```

# mdadm -vv -A /dev/md0 --uuid=edc7e813:a81d185d:95e159ea:5a1a149d
mdadm: looking for devices for /dev/md0
<SNIP - REMOVED OTHER, UNRELATED DRIVES>
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 0.
mdadm: added /dev/sdc1 to /dev/md0 as 0
mdadm: added /dev/sdd1 to /dev/md0 as 2
mdadm: added /dev/sde1 to /dev/md0 as 1
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.

```

---

### Post by karatefish on 2007-12-31
Ok, I did a lot of searching, but couldn't find a similar situation. Eventually I bit the bullet and tried to force the assemble (holding my breath and crossing my fingers)```

# mdadm -vv -Af /dev/md0 --uuid=edc7e813:a81d185d:95e159ea:5a1a149d

```

The array came back up straight away and continued with the grow process. Once it was complete, fscking the filesystems passed fine, and all my files are still there. So the solution was a fairly simple one, I just was nervous about doing it before because I was afraid it might mess something up.

---

### Post by fjgaude on 2008-01-01
Happy to see you got the array to assemble. I guess the --force option handled what likely was a superblock that was out of date. Anyway, congratulations.

Happy New Year!

---

