---
title: "Trying to recover an old NAS drive"
date: 2018-05-29
forum: General Help
---

### Post by jharrison80 on 2018-05-29
Hello, I am new to this forum and a little new to linux as well.  I used to have an Omninas that died on me taking out one of my 2 drives with it.  I have one drive that has data on it and am trying to recover it.  I'm running Ubuntu 16.04 and have the drive in the system now.

```
sudo fdisk -l /dev/sdc
Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 084E149E-FE52-4486-A8FD-F26F362FB82A

Device       Start        End    Sectors  Size Type
/dev/sdc1       34       2081       2048    1M Microsoft LDM metadata
/dev/sdc2     2082      32767      30686   15M Microsoft reserved
/dev/sdc3    32768     442367     409600  200M Linux RAID
/dev/sdc4   442368     647167     204800  100M Microsoft LDM data
/dev/sdc5   647168    2744319    2097152    1G Linux RAID
/dev/sdc6  2744320 3907029134 3904284815  1.8T Linux RAID

Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.

```

```
sudo mdadm --examine /dev/sdc1
mdadm: No md superblock detected on /dev/sdc1.
```

```
sudo mdadm --examine /dev/sdc2
mdadm: No md superblock detected on /dev/sdc2.
```

```
sudo mdadm --examine /dev/sdc3
/dev/sdc3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : bab42229:31e9298e:e7a035e9:d69c567f
           Name : 0
  Creation Time : Tue Apr 19 06:17:22 2016
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 409576 (200.02 MiB 209.70 MB)
     Array Size : 204788 (200.02 MiB 209.70 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : b228a845:c2f97752:830a3e74:88d1c4b3

    Update Time : Tue Jan  3 03:46:30 2012
       Checksum : 2f4ec5b5 - correct
         Events : 114


   Device Role : Active device 1
   Array State : .A ('A' == active, '.' == missing, 'R' == replacing)
```

```
sudo mdadm --examine /dev/sdc4
mdadm: No md superblock detected on /dev/sdc4.

```

```
sudo mdadm --examine /dev/sdc5
/dev/sdc5:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 678c6f78:1b8cbb46:262766f7:7aa58014
           Name : 3
  Creation Time : Tue Apr 19 06:17:23 2016
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 2097128 (1024.16 MiB 1073.73 MB)
     Array Size : 1048564 (1024.16 MiB 1073.73 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 09945943:4b213b66:32331d6b:aaab9b87

    Update Time : Thu Jun 14 09:30:56 2012
       Checksum : b7bc0b9f - correct
         Events : 2


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)

```

```
sudo mdadm --examine /dev/sdc6
/dev/sdc6:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 746b3b8c:d5958147:8c4b01b8:12f6c186
           Name : 1
  Creation Time : Tue Apr 19 06:17:32 2016
     Raid Level : linear
   Raid Devices : 2

 Avail Dev Size : 3904282767 (1861.71 GiB 1998.99 GB)
  Used Dev Size : 0
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=0 sectors
          State : clean
    Device UUID : baad54ef:222f00a0:2c6b6467:14d20e31

    Update Time : Tue Apr 19 06:17:32 2016
       Checksum : 7a57b629 - correct
         Events : 0

       Rounding : 0K

   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)

```

```
 sudo mount -r /dev/sdc6 /mnt/2tb
mount: unknown filesystem type 'linux_raid_member'

```

```
 sudo cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md125 : active raid1 sdc5[1]
      1048564 blocks super 1.2 [2/1] [_U]

md126 : inactive sdc6[1](S)
      1952141383 blocks super 1.2

md127 : active (auto-read-only) raid1 sdc3[1]
      204788 blocks super 1.2 [2/1] [_U]

unused devices: <none>

```

So I'm just trying to get this drive mounted so I can recover the data from it if possible.  Is there any more info I can provide?  Commands I can run?

Thanks for any help!

---

