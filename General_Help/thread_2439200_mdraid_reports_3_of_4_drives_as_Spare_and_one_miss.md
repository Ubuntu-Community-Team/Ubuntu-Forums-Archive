---
title: "mdraid reports 3 of 4 drives as Spare and one missing"
date: 2020-03-24
forum: General Help
---

### Post by svizi on 2020-03-24
Hi all,

i have a faulty mdraid (RAID 5 ?) that i am trying to troubleshoot.
The RAID has 4 1TB drives but mdadm --detail reports 3 and the 3 of them are reported as spare.

```

/dev/md0:
        Version : 1.2
     Raid Level : raid0
  Total Devices : 3
    Persistence : Superblock is persistent

          State : inactive

           Name : artemis:0  (local to host artemis)
           UUID : 09a18ebe:5c8c4e57:2a355eeb:5931941c
         Events : 41493

    Number   Major   Minor   RaidDevice

       -       8        0        -        /dev/sda
       -       8       33        -        /dev/sdc1
       -       8       49        -        /dev/sdd1


```

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd1[1](S) sdc1[6](S) sda[4](S)
      2930279514 blocks super 1.2
       
unused devices: <none>

```

Fdisk reports the following 

```
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6dc89b71

Device     Boot Start        End    Sectors   Size Id Type
/dev/sda1        2048 1953525167 1953523120 931.5G fd Linux raid autodetect


Disk /dev/sdb: 596.2 GiB, 640135028736 bytes, 1250263728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5ed586ef

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdb1  *          2048 1242943487 1242941440 592.7G 83 Linux
/dev/sdb2       1242945534 1250263039    7317506   3.5G  5 Extended
/dev/sdb5       1242945536 1250263039    7317504   3.5G 82 Linux swap / Solaris


Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0004b10c

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdc1          63 1953520064 1953520002 931.5G fd Linux raid autodetect


Disk /dev/sdd: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe09d757f

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdd1          63 1953520064 1953520002 931.5G fd Linux raid autodetect


Disk /dev/sde: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0008b2ca

Device     Boot Start        End    Sectors   Size Id Type
/dev/sde1          63 1953520064 1953520002 931.5G fd Linux raid autodetect



```

Any clues from where to start?

Thanks!

---

