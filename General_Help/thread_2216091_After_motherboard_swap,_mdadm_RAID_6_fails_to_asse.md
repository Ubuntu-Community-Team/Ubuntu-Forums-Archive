---
title: "After motherboard swap, mdadm RAID 6 fails to assemble"
date: 2014-04-10
forum: General Help
---

### Post by Erk1209 on 2014-04-10
Hello all. I recently upgraded my home server by installing a new Xeon e3-1270v3 and Supermicro X10SAT board. Installation was simple and I reconnected my controller card, a LSI 9211-8i. When I booted the array would not mount. I tried to stop and reassemble the array but was met with this: 

root@PreciseServer:~# mdadm --assemble --scan --force -v /dev/md0
mdadm: looking for devices for /dev/md0
mdadm: Cannot assemble mbr metadata on /dev/sdl1
mdadm: Cannot assemble mbr metadata on /dev/sdl
mdadm: no recogniseable superblock on /dev/sdh1
mdadm: Cannot assemble mbr metadata on /dev/sdh
mdadm: no RAID superblock on /dev/sdd1
mdadm: no RAID superblock on /dev/sdd
mdadm: no RAID superblock on /dev/sdk1
mdadm: no RAID superblock on /dev/sdk
mdadm: no RAID superblock on /dev/sdf1
mdadm: no RAID superblock on /dev/sdf
mdadm: no RAID superblock on /dev/sdj1
mdadm: no RAID superblock on /dev/sdj
mdadm: no RAID superblock on /dev/sde1
mdadm: no RAID superblock on /dev/sde
mdadm: no RAID superblock on /dev/sdi1
mdadm: no RAID superblock on /dev/sdi
mdadm: no RAID superblock on /dev/sda5
mdadm: no RAID superblock on /dev/sda2
mdadm: no RAID superblock on /dev/sda1
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sdg is identified as a member of /dev/md0, slot 7.
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdb is identified as a member of /dev/md0, slot 8.
mdadm: no uptodate device for slot 0 of /dev/md0
mdadm: no uptodate device for slot 2 of /dev/md0
mdadm: no uptodate device for slot 3 of /dev/md0
mdadm: no uptodate device for slot 4 of /dev/md0
mdadm: no uptodate device for slot 5 of /dev/md0
mdadm: no uptodate device for slot 6 of /dev/md0
mdadm: added /dev/sdg to /dev/md0 as 7
mdadm: added /dev/sdb to /dev/md0 as 8
mdadm: no uptodate device for slot 9 of /dev/md0
mdadm: added /dev/sdc to /dev/md0 as 1
mdadm: /dev/md0 assembled from 3 drives - not enough to start the array.

The array is supposed to be ten drives in a RAID 6. I did not partition the drives when I created the array and have been growing the array by adding whole disks as I've gone. Can someone help me understand what happened? Even better, could someone help me correct the problem so I can get my array running again?

Thanks so much for your time!

---

### Post by Erk1209 on 2014-04-10
Here is some additional output:

root@PreciseServer:~# mdadm --detail /dev/md0
mdadm: cannot open /dev/md0: No such file or directory
root@PreciseServer:~# mdadm --assemble /dev/md0
mdadm: /dev/md0 assembled from 3 drives - not enough to start the array.
root@PreciseServer:~# mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.

______________________________________________________________

root@PreciseServer:~# mdadm --examine /dev/sdd
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
root@PreciseServer:~# mdadm --examine /dev/sdd1
mdadm: No md superblock detected on /dev/sdd1.
root@PreciseServer:~# 

-----------------------------------------------------------------

root@PreciseServer:~# parted /dev/sdd print
Model: ATA ST2000DM001-9YN1 (scsi)
Disk /dev/sdd: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2000GB  2000GB                     raid

----------------------------------------------------------------

I would be very grateful for a hand in correcting this issue

---

### Post by Erk1209 on 2014-04-10
Here is the output from a drive that is still properly a RAID component:

root@PreciseServer:~# mdadm --examine /dev/sdg
/dev/sdg:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : dff1c3d6:8528c4ba:5df0c08b:33a1a043
           Name : PreciseServer:0
  Creation Time : Sat Jul  7 15:34:42 2012
     Raid Level : raid6
   Raid Devices : 10

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 15628103680 (14904.12 GiB 16003.18 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : d80a5ff5:5ec7aa85:422aaa1e:f6819dc2

    Update Time : Tue Apr  8 19:07:45 2014
       Checksum : 3dd924dd - correct
         Events : 15986

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 7
   Array State : AAAAAAAAAA ('A' == active, '.' == missing)

---

### Post by Erk1209 on 2014-04-10
mdadm --examine /dev/sd* output:

root@PreciseServer:~# mdadm --examine /dev/sd*
/dev/sda:
   MBR Magic : aa55
Partition[0] :    218228736 sectors at         2048 (type 83)
Partition[1] :     16210864 sectors at    218230784 (type 05)
mdadm: No md superblock detected on /dev/sda1.
/dev/sda2:
   MBR Magic : aa55
Partition[0] :     16207872 sectors at         2048 (type 82)
mdadm: No md superblock detected on /dev/sda5.
/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : dff1c3d6:8528c4ba:5df0c08b:33a1a043
           Name : PreciseServer:0
  Creation Time : Sat Jul  7 15:34:42 2012
     Raid Level : raid6
   Raid Devices : 10

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 15628103680 (14904.12 GiB 16003.18 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : cff1ced2:6d154a19:4ded798d:b90ee7d2

    Update Time : Tue Apr  8 19:07:45 2014
       Checksum : 2e01a9b5 - correct
         Events : 15986

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 8
   Array State : AAAAAAAAAA ('A' == active, '.' == missing)
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : dff1c3d6:8528c4ba:5df0c08b:33a1a043
           Name : PreciseServer:0
  Creation Time : Sat Jul  7 15:34:42 2012
     Raid Level : raid6
   Raid Devices : 10

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 15628103680 (14904.12 GiB 16003.18 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 24238470:0407192c:7768dfcd:ed35abf6

    Update Time : Tue Apr  8 19:07:45 2014
       Checksum : 42af6f00 - correct
         Events : 15986

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAAAAAAAAA ('A' == active, '.' == missing)
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sdd1.
/dev/sde:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sde1.
/dev/sdf:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sdf1.
/dev/sdg:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : dff1c3d6:8528c4ba:5df0c08b:33a1a043
           Name : PreciseServer:0
  Creation Time : Sat Jul  7 15:34:42 2012
     Raid Level : raid6
   Raid Devices : 10

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 15628103680 (14904.12 GiB 16003.18 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : d80a5ff5:5ec7aa85:422aaa1e:f6819dc2

    Update Time : Tue Apr  8 19:07:45 2014
       Checksum : 3dd924dd - correct
         Events : 15986

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 7
   Array State : AAAAAAAAAA ('A' == active, '.' == missing)
/dev/sdh:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sdh1.
/dev/sdi:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sdi1.
/dev/sdj:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sdj1.
/dev/sdk:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sdk1.
/dev/sdl:
   MBR Magic : aa55
Partition[0] :     15636801 sectors at           63 (type 0c)
/dev/sdl1:
   MBR Magic : aa55
Partition[0] :   1851859059 sectors at   1936028272 (type 68)
Partition[1] :    538976288 sectors at   1330184192 (type 79)
Partition[2] :   1398362912 sectors at    538989391 (type 53)
Partition[3] :        21337 sectors at   1394627663 (type 49)


I do not understand where that /dev/sdl came from as the disks in my machine only go up to /dev/sdk...

---

### Post by frostschutz on 2014-04-11
If all those disks were unpartitioned, like the ones that still have metadata. It seems that something created a GPT partition label on your disks, overwriting the mdadm metadata in the process. That leaves you a raid with 7 failed drives, which is completely useless.

The question is, how did this happen? And what else happened? If the creation of a partition table was the only thing that happened, you may be able to salvage something with some effort (the drive order is unknown and with 7 drives there are a lot of possibilities).

However if in addition to the creation of partition, other data was written as well (such as formatting of filesystems, etc.), then you have very little chances of recovery.

Do you have a backup? Was the data on the RAID encrypted?

The method here in general is to find a plain/known type file that is larger than chunk size times disks (i.e. in your case 512kb * 10) and then deduce the drive order / raid layout from that, either manually or by writing a script that goes through all possible drive orders... there is no tool that solves this puzzle for you, or at least, I don't know such a tool.

---

