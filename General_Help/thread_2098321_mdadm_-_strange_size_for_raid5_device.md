---
title: "mdadm - strange size for raid5 device?"
date: 2012-12-26
forum: General Help
---

### Post by tobiasgardner on 2012-12-26
Hi, I have three (3) 3TB disks that make up one raid5 device. However, it only seems to have ~4TB of useable space... I think it should have ~6TB... Anyone who can explain why?!

```

root@nas:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sat Dec 22 08:36:48 2012
     Raid Level : raid5
     Array Size : 4294702080 (4095.75 GiB 4397.77 GB)
  Used Dev Size : 2147351040 (2047.87 GiB 2198.89 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Wed Dec 26 13:29:51 2012
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : nas:0  (local to host nas)
           UUID : bca128c7:dd841b96:26ce92d0:3bc40947
         Events : 20

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       3       8       33        2      active sync   /dev/sdc1

```

```

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
/dev/sda1            2048  4294967294  2147482623+  fd  Linux raid autodetect
Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
/dev/sdb1            2048  4294967294  2147482623+  fd  Linux raid autodetect
Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
/dev/sdc1            2048  4294967294  2147482623+  fd  Linux raid autodetect
Disk /dev/md0: 4397.8 GB, 4397774929920 bytes

```

Looking at fdisk -l details for one of the devices used for the raid5 device:

```

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
90 heads, 3 sectors/track, 21705678 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x4641c27b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  4294967294  2147482623+  fd  Linux raid autodetect

```

Regards, Tobbe G

---

### Post by Cheesemill on 2012-12-26
It's because the drives are formatted with an msdos partition table.

For large drives you have to use the newer GPT type partition table for more than 2TB to be recognised properly.

---

### Post by tobiasgardner on 2012-12-26
So... I need to destroy my raid set and format the disks PRIOR to creating the RAID set?

I used fdisk to set the type to "Linux raid autodetect" before building the RAID set...

---

### Post by Cheesemill on 2012-12-26
fdisk only works on drives with the old msdos partition table, instead you need to use gdisk (or cgdisk).

Just running gdisk on a drive should automatically convert the partitioning to GPT without any data loss, just have a backup first just in case.
I'm not sure whether or not mdadm will pick up on the change though so you *may* need to recreate the array afterwards.

```
sudo apt-get install gdisk
sudo gdisk /dev/sda
```

---

### Post by tobiasgardner on 2012-12-26
Using gdisk, shall I set the type to fd00 (Linux RAID) when using mdadm?

---

### Post by SaturnusDJ on 2012-12-26
When using the entire hdd it's more easy to use 'no partition' and leave it to mdadm. Just create the array from /dev/sd[a-c].

---

### Post by SaturnusDJ on 2013-02-17
> **SaturnusDJ said:**
> When using the entire hdd it's more easy to use 'no partition' and leave it to mdadm. Just create the array from /dev/sd[a-c].

I'm wrong on this one.
Read here why: [http://ubuntuforums.org/showpost.php?p=12484473&postcount=8](http://ubuntuforums.org/showpost.php?p=12484473&postcount=8)

---

