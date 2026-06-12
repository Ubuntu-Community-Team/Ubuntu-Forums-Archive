---
title: "ext4, bad group descriptors raid 6."
date: 2014-01-23
forum: General Help
---

### Post by abeed on 2014-01-23
Hello, I am a total linux/computer noob. Im using a ubuntu 12.04 system a friend built for me years ago.
I have a 8 x 3tb western digital green raid 6. Upon returning from a vacation, I fired up the machine to find no raid? I've scoured google for a week and now I'm unsure how to proceed.

Please help.


```
mdadm --detail /dev/md0/dev/md0:
        Version : 1.2
  Creation Time : Wed Nov 23 00:18:44 2011
     Raid Level : raid6
     Array Size : 17581581312 (16767.10 GiB 18003.54 GB)
  Used Dev Size : 2930263552 (2794.52 GiB 3000.59 GB)
   Raid Devices : 8
  Total Devices : 8
    Persistence : Superblock is persistent


    Update Time : Thu Jan 23 22:54:19 2014
          State : clean 
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric-6
     Chunk Size : 512K


           Name : abeed-raid:0
           UUID : 49d9b11b:f3cf7d55:d8f4cb4a:cde2acc5
         Events : 15138


    Number   Major   Minor   RaidDevice State
       4       8       81        0      active sync   /dev/sdf1
       1       8       97        1      active sync   /dev/sdg1
       3       8      129        2      active sync   /dev/sdi1
       8       8       65        3      active sync   /dev/sde1
       7       8       49        4      active sync   /dev/sdd1
       6       8        1        5      active sync   /dev/sda1
       5       8       17        6      active sync   /dev/sdb1
       9       8       33        7      active sync   /dev/sdc1



```

The Raid seems to be assembled perfectly. (could the order have changed itself?? as far as I know, no rebuild or reshape took place.)
I always had a problem creating a file system larger than 16 TB, so I ended up making a partition: md0p1 being 16TB and the rest unallocated. Yet now I only see md0 ?

The issue is in mounting it

```
mount /dev/md0 /raidmount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



```

Im pretty sure it was md0p1 previously, but it was added into fstab as a UUID which doesnt seem to exist anymore.

```
UUID=aabada66-961b-4673-9a1e-f8a88c4b37a7 /               ext4    errors=remount-ro 0       1


```

blkid

```
/dev/sdh1: UUID="0257bd03-fbc0-4fad-a827-65d84db6cace" TYPE="ext4" /dev/sdh2: UUID="aabada66-961b-4673-9a1e-f8a88c4b37a7" TYPE="ext4" 
/dev/md0: UUID="1a6c386e-a8fc-4570-9083-fca75c5eccf6" TYPE="ext4" 
```

And lastly dmesg | tail 

```
[ 1231.968085] ata2.00: failed command: IDENTIFY DEVICE[ 1231.968091] ata2.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[ 1231.968093]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 1231.968096] ata2.00: status: { DRDY }
[ 1231.968101] ata2: hard resetting link
[ 1232.460034] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 1232.461840] ata2.00: configured for UDMA/133
[ 1232.461897] ata2: EH complete
[ 2705.129469] EXT4-fs (md0): ext4_check_descriptors: Block bitmap for group 32640 not in group (block 517427200)!
[ 2705.129473] EXT4-fs (md0): group descriptors corrupted!


 
```

Thanks.

---

