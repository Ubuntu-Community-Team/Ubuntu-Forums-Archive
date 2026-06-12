---
title: "Mount raid1 on Ubuntu 22.04LTS"
date: 2023-12-24
forum: General Help
---

### Post by asb3 on 2023-12-24
I had two disks mounted as a raid1 system.  I can no longer mount them.
The drive seem to be OK.
```

> lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
sdb      1.8T                 disk 
&#9492;&#9472;sdb1   1.8T linux_raid_memb part 
sdc      1.8T                 disk 
&#9492;&#9472;sdc1   1.8T linux_raid_memb part 

> sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 3ccb83f1:00966ecf:c76168c2:1dc77397
           Name : cavu:0
  Creation Time : Wed Sep 30 02:25:38 2020
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 3906762752 sectors (1862.89 GiB 2000.26 GB)
     Array Size : 1953381376 KiB (1862.89 GiB 2000.26 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=0 sectors
          State : clean
    Device UUID : 195d4ec3:1673cbf3:f1dd2c6c:c2f3f082

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Oct 30 10:08:21 2023
  Bad Block Log : 512 entries available at offset 16 sectors
       Checksum : 76226c0f - correct
         Events : 35087
   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)

> sudo mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 3ccb83f1:00966ecf:c76168c2:1dc77397
           Name : cavu:0
  Creation Time : Wed Sep 30 02:25:38 2020
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 3906762752 sectors (1862.89 GiB 2000.26 GB)
     Array Size : 1953381376 KiB (1862.89 GiB 2000.26 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=0 sectors
          State : clean
    Device UUID : c5d8be31:bd7625ec:92bc8154:8b61969f

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Oct 30 10:08:21 2023
  Bad Block Log : 512 entries available at offset 16 sectors
       Checksum : e1e737cc - correct
         Events : 35087


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)

```

How do I mount these as a raid1, or. alternatively, retrieve data from either drive?

---

### Post by asb3 on 2023-12-24
There is an mdadm file:
> 
# mdadm.conf
#
# !NB! Run update-initramfs -u after updating this file.
# !NB! This will ensure that initramfs has an uptodate copy.
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
ARRAY /dev/md/0  metadata=1.2 UUID=3ccb83f1:00966ecf:c76168c2:1dc77397 name=cavu:0

# This configuration was auto-generated on Sun, 24 Dec 2023 02:14:00 -0500 by mkconf



There is no directory
/dev/md.

---

### Post by asb3 on 2023-12-24
I got the raid to mount with the command
```

> sudo mdadm -- assemble --scan
mdadm: /dev/md/0 has been started with 2 drives

```

I'm somewhat confused about where the volume was mounted.
/dev/md/0 is a link to /dev/md0.
/dev/md0 is unreadable.

The volume is mounted in
/media/asb/d6c5cad7-48ee-4211-8570-a6d771650a87

I have no idea where that mount point came from.

---

