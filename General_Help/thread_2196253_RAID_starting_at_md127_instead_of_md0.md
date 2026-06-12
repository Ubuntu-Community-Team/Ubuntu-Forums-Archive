---
title: "RAID starting at md127 instead of md0"
date: 2013-12-28
forum: General Help
---

### Post by Virtual_Ron on 2013-12-28
(Sorry for starting a new thread, but I'm having this issue, and other threads were closed)

I'm having the issue that I see many are experiancing.     I just upgraded to Ubuntu 13.04 (from 12.10), and my mdadm created RAID stopped working.

my RAID was at /dev/md0, but after reboot...

```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : inactive sdd1[2](S)
      976629760 blocks super 1.2
       
md1 : inactive sdb1[0]
      976629760 blocks super 1.2

```

So, I stop them: **sudo mdadm --stop /dev/md127 & sudo mdadm --stop /dev/md1**
then reassemle my RAID:  **sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sde1**

```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[0] sde1[3] sdc1[1]
      1953258496 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>

```

```

sudo mdadm --detail /dev/md0

/dev/md0:
        Version : 1.2
  Creation Time : Sun Jul 21 08:00:38 2013
     Raid Level : raid5
     Array Size : 1953258496 (1862.77 GiB 2000.14 GB)
  Used Dev Size : 976629248 (931.39 GiB 1000.07 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Sat Dec 28 15:16:12 2013
          State : clean 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : vulcan:1  (local to host vulcan)
           UUID : 48f99272:3c964cb3:fc6872f2:72de5f7f
         Events : 35

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       3       8       65        2      active sync   /dev/sde1

```

```
sudo mdadm --detail --scan
ARRAY /dev/md0 metadata=1.2 name=vulcan:1 UUID=48f99272:3c964cb3:fc6872f2:72de5f7f

```

eveything looks good, and I can mount /dev/md0  so....

I append THAT info to my mdadm.conf file, but following other's advice, removed the "metadata= and name=" tags:

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 UUID=48f99272:3c964cb3:fc6872f2:72de5f7f

```

Then I run the comand:   **sudo update-initramfs -u**
and reboot...

it does not fix the issue, and the cycle repeats.  I'm dumped out to busybox initramfs.

Any suggestions?   

Many thanks!

Ron

---

