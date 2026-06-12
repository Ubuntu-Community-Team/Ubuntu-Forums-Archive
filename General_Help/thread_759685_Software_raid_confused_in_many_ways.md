---
title: "Software raid confused in many ways"
date: 2008-04-19
forum: General Help
---

### Post by rm-rf on 2008-04-19
On my system there was an OS disk on /dev/sda plus five disks on a software RAID five spanning /dev/sd{b-f}1.

Then I inserted a new disk to mirror the OS disks, which renamed my disks /dev/sda (primary OS), /dev/sdb (secondary, for OS) and my RAID disks became /dev/sd{c-g}1. Long story short the raid refuses to come up.

This is what happens when I try to assemble:
```
# mdadm --assemble --verbose /dev/md0 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdg1 is identified as a member of /dev/md0, slot 4.
mdadm: added /dev/sdc1 to /dev/md0 as 0
mdadm: added /dev/sdd1 to /dev/md0 as 1
mdadm: added /dev/sde1 to /dev/md0 as 2
mdadm: added /dev/sdf1 to /dev/md0 as 3
mdadm: added /dev/sdg1 to /dev/md0 as 4
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.

```

I think the following is showing me what mdadm 'thinks' things should be:
```
# mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : ab6e41e0:e374277d:9ae343a0:299f2bc8
  Creation Time : Sat Apr 19 00:56:52 2008
     Raid Level : raid5
    Device Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1953535744 (1863.04 GiB 2000.42 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Sat Apr 19 06:25:31 2008
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : a9bf2603 - correct
         Events : 0.6

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
 
```

So I guess that with the new device names the UUIDs on the drives changed? How dow I fix it so I can mount the darn RAID?

---

### Post by fjgaude on 2008-04-19
From what you write and what I see here I think all you have to do is this:

```
sudo mdadm --assemble --scan
```

That should do it. mdadm doesn't really use the name of drives to assemble. It scans the superblocks to see how the drives were initialy created to form the array. It never forget this, and you can mount the array from motherboard to motherboard with different number of drives and it will still assemble. You have to let it do its thing, and not tell it what drives to you as you did.

After all this, try the -D command to see if everything is as it should be:

```
sudo mdadme -D /dev/md0
```

Let us know how you make out.

---

### Post by rm-rf on 2008-04-19
[QUOTE=fjgaude;4748169]From what you write and what I see here I think all you have to do is this:

```
sudo mdadm --assemble --scan
```

I tried that but I get the following:
```
sudo mdadm --assemble --scan
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.
```
Which is the same error i get when running the full blown command. Could this be because just one of the drives matched its original UUID? I mean, the full blown command can see the drives as belonging to a raid device.

---

