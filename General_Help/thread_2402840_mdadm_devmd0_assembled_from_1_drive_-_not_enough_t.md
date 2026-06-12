---
title: "mdadm: /dev/md0 assembled from 1 drive - not enough to start the array."
date: 2018-10-04
forum: General Help
---

### Post by backspin on 2018-10-04
I have a 3 disc array, and one disc failed. However, after unplugging what I thought was the bad drive and starting back up, the array went inactive.  I decided to plug the faulty drive back in and it now shows good, but the array is still inactive. 

I haven't been able to get the array out of inactive, and have tried a couple of different ways.

```

root@pc2:~# mdadm --detail /dev/md0
/dev/md0:
           Version : 1.2
        Raid Level : raid0
     Total Devices : 3
       Persistence : Superblock is persistent


             State : inactive
   Working Devices : 3


              Name : pc2:0  (local to host pc2)
              UUID : ff8b73cc:c3f4ce8e:9d5d7be2:b406e0cc
            Events : 403123


    Number   Major   Minor   RaidDevice


       -       8       32        -        /dev/sdc
       -       8        0        -        /dev/sda
       -       8       16        -        /dev/sdb

```

When I try to assemble the array whilst I get a compleaint about the config file.

```

root@pc2:~# mdadm --assemble --scan -v /dev/sd[abc]
mdadm: /dev/sda not identified in config file.
mdadm: /dev/sdb not identified in config file.
mdadm: /dev/sdc not identified in config file.

```

This is the mdadm.conf

```

root@pc2:~# cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays


# This configuration was auto-generated on Fri, 13 Oct 2017 20:58:03 -0500 by mkconf
ARRAY /dev/md0 metadata=1.2 name=pc2:0 UUID=ff8b73cc:c3f4ce8e:9d5d7be2:b406e0cc
#ARRAY /dev/md/0  metadata=1.2 UUID=ff8b73cc:c3f4ce8e:9d5d7be2:b406e0cc name=pc2:0
#ARRAY /dev/md/0  metadata=1.2 UUID=ff8b73cc:c3f4ce8e:9d5d7be2:b406e0cc name=pc2:0

```

When I stop the array, and try to assemble, that's when it says -- "mdadm: /dev/md0 assembled from 1 drive - not enough to start the array."

Let me know if there's more information needed or additional command run.

*EDIT* Additional Info

This is what happens when I stop the array and try to assemble.

root@pc2:~# mdadm --stop /dev/md0
mdadm: stopped /dev/md0





```

root@pc2:~# mdadm --assemble --scan -v /dev/md0
mdadm: looking for devices for /dev/md0
-OMIT all the other devices that do not match -OMIT
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdb is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sda is identified as a member of /dev/md0, slot 1.
mdadm: added /dev/sda to /dev/md0 as 1 (possibly out of date)
mdadm: added /dev/sdc to /dev/md0 as 2 (possibly out of date)
mdadm: added /dev/sdb to /dev/md0 as 0
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.

```

---

### Post by backspin on 2018-10-05
continuation as I've made progress.

I've managed to bring the array back to active. I did it by stopping the array and then issuing the --force command.
```

mdadm --assemble -v /dev/md0 /dev/sd[abc] --force

```

```

root@pc2:~# mdadm --detail /dev/md0
/dev/md0:
           Version : 1.2
     Creation Time : Fri Oct 13 21:06:05 2017
        Raid Level : raid5
        Array Size : 5860270080 (5588.79 GiB 6000.92 GB)
     Used Dev Size : 2930135040 (2794.39 GiB 3000.46 GB)
      Raid Devices : 3
     Total Devices : 2
       Persistence : Superblock is persistent


     Intent Bitmap : Internal


       Update Time : Fri Oct  5 18:45:04 2018
             State : clean, degraded 
    Active Devices : 2
   Working Devices : 2
    Failed Devices : 0
     Spare Devices : 0


            Layout : left-symmetric
        Chunk Size : 512K


Consistency Policy : bitmap


              Name : pc2:0  (local to host pc2)
              UUID : ff8b73cc:c3f4ce8e:9d5d7be2:b406e0cc
            Events : 403134


    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       -       0        0        1      removed
       3       8       32        2      active sync   /dev/sdc

```

Okay, so I'm back to where I was originally with 1 dead drive. However, I thought I pulled the correct drive and I was wrong.  I don't have any lights on these drives, and all 3 are spinning. How do I tell which drive is plugged into which sata port on the motherboard?

```

root@pc2:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb[0] sdc[3]
      5860270080 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [U_U]
      bitmap: 4/22 pages [16KB], 65536KB chunk

```

---

### Post by backspin on 2018-10-05
Okay... I have identified sda by serial number by running this command.

```

hdparm -i /dev/sda

```

I'm now going to shut down the machine and find the bad disc by serial number. Then plug/install the new disc, and boot up.

---

### Post by backspin on 2018-10-05
Lastly, I pulled the cover off the machine, and found the hard drive with the matching serial number. Installed the new drive, and boot up.

From command line, issued this command to join the new disc.

```

mdadm --add /dev/md0 /dev/sda

```

And am now watching the 3rd disk rebuild using the watch command. We can see below the disk is rebuilding. 

```

Every 2.0s: cat /proc/mdstat                                                                                    pc2: Fri Oct  5 19:42:16 2018


Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10]
md0 : active raid5 sda[4] sdb[0] sdc[3]
      5860270080 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [U_U]
      [>....................]  recovery =  1.7% (50331832/2930135040) finish=307.3min speed=156155K/sec
      bitmap: 4/22 pages [16KB], 65536KB chunk


unused devices: <none>

```

Over-all the issue I had was when the drive went inactive, and mdadm said that it could not start because there was only 1 disk in which to build (scary).  However, using the --force command got the array up with 2 drives and the rest is history.

---

### Post by Yellow Pasque on 2018-10-06
I was confused when I saw RAID0

```
        Raid Level : raid0
```

Obviously, if you have a disk die in RAID0, you are not rebuilding the array unless you have backup.

---

### Post by backspin on 2018-10-06
> **Temüjin said:**
> I was confused when I saw RAID0

```
        Raid Level : raid0
```

Obviously, if you have a disk die in RAID0, you are not rebuilding the array unless you have backup.

A totally scary situation when the array goes inactive, and won't assemble because there's only 1 drive in which to build..... AND says raid0.  I think this came down to operator error on my part for pulling the wrong disk.  The array took 5 hours or so to rebuild, and haven't had any problems since.

---

