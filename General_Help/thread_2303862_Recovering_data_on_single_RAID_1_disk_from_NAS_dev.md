---
title: "Recovering data on single RAID 1 disk from NAS device"
date: 2015-11-22
forum: General Help
---

### Post by dave210 on 2015-11-22
I've just about done my head in, reading and re-reading the same posts; trying and retrying the same things (in different orders) hoping for a different outcome.  (One of the definitions of insanity, isn't it?)  Time to call first-hand upon the wisdom of the forums!

My situation is this:
[LIST]
[*]Thecus N0204 minNAS device - has been working a treat for years, and just gave up the ghost the other week.  Won't boot.  Device is dead. 
[*]"Critical" data backed up to a separate device - I've already reinstated that. 
[*]"Really important" data, I now realise, remains on the two 2.5" HDDs from the NAS - and I really do need to retrieve it. 
[*]Freshly installed Ubuntu 12.04 (not live CD - I tried that a few times over the weeks and got sick of the boot process!) 
[*]I have a SATA-to-USB adapter which I'm using to connect one of the RAID 1 disks to the PC for analysis (and data recovery - hopefully!) 
[/LIST]

Reading up on Thecus NAS recovery, and mdadm RAID recovery using a single disk from a RAID 1 array, I think I have all the pieces in place.  But connecting them all together still eludes me.  If somebody could tell me the magic command(s) that I'm missing, I would very much appreciate it!

Diagnostics as follows:

[B]blkid
[/B]sda is the PC boot disk.  USB device (sdb) doesn't show up here.
```
root@dell9400:/home/dave# blkid
/dev/sda1: UUID="be1c2e0e-82e5-4419-8550-2d4cc604881a" TYPE="ext4"
/dev/sda5: UUID="9a15b1e9-4b7f-4727-a2a2-ceae2034209a" TYPE="swap"

```

**mdadm --assemble**
```
root@dell9400:/home/dave# mdadm --assemble --scan --verbose
mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/sdb3
mdadm: no recogniseable superblock on /dev/sdb2
mdadm: no recogniseable superblock on /dev/sdb1
mdadm: no recogniseable superblock on /dev/sdb
mdadm: cannot open device /dev/sr0: No medium found
mdadm: no recogniseable superblock on /dev/sda5
mdadm: Cannot assemble mbr metadata on /dev/sda2
mdadm: no recogniseable superblock on /dev/sda1
mdadm: Cannot assemble mbr metadata on /dev/sda
mdadm: No arrays found in config file or automatically

```

[B]cat /proc/mdstat (original)
[/B]```
root@dell9400:/home/dave# cat /proc/mdstat
Personalities :
unused devices: <none>

```
[B]cat /proc/mdstat (current)
[/B]OK, confession time.  I did try a "mdadm --create" during my fiddling, and that seems to have left its mark in the /proc/mdstat file...  (I don't know if this is significant, btw)
```
root@dell9400:/home/dave# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
unused devices: <none>

```[B]

fdisk -l /dev/sdb*
[/B]I've convinced myself that /dev/sdb2 is the data partition I'm trying to recover```
root@dell9400:/home/dave# fdisk -l /dev/sdb*
Note: sector size is 4096 (not 512)
 
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 15200 cylinders, total 244190646 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     4016249    16064748   fd  Linux RAID autodetect
/dev/sdb2         5028345  1953487934  3498871064   fd  Linux RAID autodetect
/dev/sdb3         4016250     5028344     4048380   fd  Linux RAID autodetect
 
Partition table entries are not in disk order
Note: sector size is 4096 (not 512)
 
Disk /dev/sdb1: 16.5 GB, 16450301952 bytes
255 heads, 63 sectors/track, 249 cylinders, total 4016187 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000005
 
Disk /dev/sdb1 doesn't contain a valid partition table
Note: sector size is 4096 (not 512)
 
Disk /dev/sdb2: 979.6 GB, 979608784896 bytes
255 heads, 63 sectors/track, 14887 cylinders, total 239162301 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc82bae54
 
Disk /dev/sdb2 doesn't contain a valid partition table
Note: sector size is 4096 (not 512)
 
Disk /dev/sdb3: 4145 MB, 4145541120 bytes
255 heads, 63 sectors/track, 63 cylinders, total 1012095 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xb183db6c
 
Disk /dev/sdb3 doesn't contain a valid partition table

```

**disktype**
```
root@dell9400:/home/dave# disktype /dev/sdb
 
--- /dev/sdb
Block device, size 931.5 GiB (1000204886016 bytes)
DOS/MBR partition map
Partition 1: 1.915 GiB (2056287744 bytes, 4016187 sectors from 63)
  Type 0xFD (Linux raid autodetect)
  Linux RAID disk, version 0.90.0
    RAID1 set using 4 regular -2 spare disks
    RAID set UUID 3FA9568B-8558-26AD-4D3D-F65A272836F3 (NCS)
  Linux swap, version 2, subversion 1, 4 KiB pages, little-endian
    Swap size 1.915 GiB (2056183808 bytes, 501998 pages of 4 KiB)
Partition 2: 929.1 GiB (997611310080 bytes, 1948459590 sectors from 5028345)
  Type 0xFD (Linux raid autodetect)
  Linux RAID disk, version 0.90.0
    RAID1 set using 2 regular -1 spare disks
    RAID set UUID 194009F8-E7DD-2B55-922F-FE2ECD8892D1 (DCE, v2)
  XFS file system, version 4
    Volume name ""
    UUID E97CE4B8-81CF-47B9-940F-92C231DF8437 (DCE, v4)
    Volume size 929.1 GiB (997611208704 bytes, 243557424 blocks of 4 KiB)
Partition 3: 494.2 MiB (518192640 bytes, 1012095 sectors from 4016250)
  Type 0xFD (Linux raid autodetect)
  Linux RAID disk, version 0.90.0
    RAID1 set using 2 regular 0 spare disks
    RAID set UUID 7E3D5413-A2F6-AD50-0F3C-0CFC5637F864 (NCS)
  Minix file system (v2, 30 chars)
    Volume size 490.0 MiB (513794048 bytes, 501752 blocks of 1 KiB)

```

[B]mdadm -Cv /dev/md0 -l1 -n2 /dev/sdb2 missing
[/B]OK - here's where I got ambitious with "mdadm --create".  It did something - but no joy.  And I'm concerned that I may have made a mistake - possibly should have used "mdadm --build" instead??

```
root@dell9400:/home/dave# mdadm -Cv /dev/md0 -l1 -n2 /dev/sdb2 missing
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
mdadm: size set to 956517952K
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.

```

[B]mdadm --detail
[/B]```
root@dell9400:/home/dave# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sun Nov 22 13:03:55 2015
     Raid Level : raid1
     Array Size : 956517952 (912.21 GiB 979.47 GB)
  Used Dev Size : 956517952 (912.21 GiB 979.47 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent
 
    Update Time : Sun Nov 22 13:28:30 2015
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0
 
           Name : dell9400:0  (local to host dell9400)
           UUID : d5778721:4524ed34:93181a64:49af8e08
         Events : 8
 
    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       0        0        1      removed

```

**mount**
No good  :(
```
root@dell9400:/home/dave# mount /dev/md0 /mnt
mount: you must specify the filesystem type
root@dell9400:/home/dave# mount -t xfs /dev/md0 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
 
root@dell9400:/home/dave# **dmesg |tail**
[14347.874435] sd 3:0:0:0: [sdb] Bad block number requested
[14347.874457] sd 3:0:0:0: [sdb] Bad block number requested
[14347.874478] sd 3:0:0:0: [sdb] Bad block number requested
[14347.874499] sd 3:0:0:0: [sdb] Bad block number requested
[14360.246456] EXT3-fs (md0): error: can't find ext3 filesystem on dev md0.
[14360.264855] EXT4-fs (md0): VFS: Can't find ext4 filesystem
[14367.377282] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[14367.380510] SGI XFS Quota Management subsystem
[14367.381952] XFS (md0): bad magic number
[14367.381957] XFS (md0): SB validate failed

```

[B]mdadm --examine
[/B]```
root@dell9400:/home/dave# mdadm -E /dev/sdb2
/dev/sdb2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : d5778721:4524ed34:93181a64:49af8e08
           Name : dell9400:0  (local to host dell9400)
  Creation Time : Sun Nov 22 13:03:55 2015
     Raid Level : raid1
   Raid Devices : 2
 
 Avail Dev Size : 1913036264 (912.21 GiB 979.47 GB)
     Array Size : 956517952 (912.21 GiB 979.47 GB)
  Used Dev Size : 1913035904 (912.21 GiB 979.47 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 538aaf6c:aefb3470:a14cc36d:9c2cf3b9
 
    Update Time : Sun Nov 22 17:40:31 2015
       Checksum : 9df358d8 - correct
         Events : 12
 
 
   Device Role : Active device 0
   Array State : A. ('A' == active, '.' == missing)

```


Other attempts have included:
**mdadm --stop**  followed by  **--build**

```
root@dell9400:/home/dave# **mdadm --remove /dev/md0**
root@dell9400:/home/dave# **mdadm --stop /dev/md0**
mdadm: stopped /dev/md0

root@dell9400:/home/dave# **mdadm --zero-superblock /dev/sdb2**
root@dell9400:/home/dave# **mdadm -E /dev/sdb2**
mdadm: No md superblock detected on /dev/sdb2.

root@dell9400:/home/dave#** mdadm -Bv /dev/md0 -l1 -n2 /dev/sdb2 missing**
mdadm: array /dev/md0 built and started.
root@dell9400:/home/dave# **mdadm -D /dev/md0**
/dev/md0:
        Version :
  Creation Time : Sun Nov 22 17:53:01 2015
     Raid Level : raid1
     Array Size : 956649204 (912.33 GiB 979.61 GB)
  Used Dev Size : 956649204 (912.33 GiB 979.61 GB)
   Raid Devices : 2
  Total Devices : 1
 
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0
 
    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       0        0        1      removed

root@dell9400:/home/dave# **mdadm -E /dev/md0**
mdadm: No md superblock detected on /dev/md0.
root@dell9400:/home/dave#** mdadm -E /dev/sdb2**
mdadm: No md superblock detected on /dev/sdb2.
root@dell9400:/home/dave# **mount /dev/md0 /mnt**
mount: you must specify the filesystem type
root@dell9400:/home/dave# **mount -t xfs /dev/md0 /mnt**
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

**_In conclusion_**
I'm stuck in a mindless loop!  Please help!

Cheers,
Dave

---

### Post by tgalati4 on 2015-11-22
What specifically failed on the NAS?  If it was a power supply, then get a new power supply.  If one disk went bad, get a new disk and reimage.  If the chassis/motherboard went bad, get a new one and migrate your disks.

I'm not convinced that this NAS uses a Debian-based operating system or uses *mdadm *to run the RAID1.  There are many flavors of linux, so what flavor of linux does this NAS run?  Is the RAID hardware-based or is it software-based?

I did a quick search of the Thecus forums and I could not find these answers.

Sometimes when you hit a wall you need to back up and examine your assumptions.

Welcome to the forums.

---

### Post by dave210 on 2015-11-23
Thanks for the reply, tgalati4,

Power supply is fine.  I believe the failure is chassis/motherboard related.  I get a single green power light on power up, and no other boot activity.

I did consider the "replace the device" option before anything.  Problem is, that model is now more than 6 years old, and I can't find anywhere that sells them.  (OK, I haven't trawled the entire universe of online shopping yet, but I believe it will be extremely difficult, if not impossible, to find a vendor.)

Flavour of linux?  Hardware or software RAID?  I too have struggled to find answers to these questions.  I'll keep prodding at the Thecus forums to see if somebody can shed some light.

In the mean time, are you suggesting that there is no way to diagnose the disk type / contents without knowing the NAS specifications?

I was hoping that the (apparently) authoritative info from disktype and fdisk would hold sufficent DNA to support a positive identification.  Is this not the case?

Cheers,
Dave

---

### Post by tgalati4 on 2015-11-23
If the Thecus NAS uses hardware RAID, then the striping is controlled by the motherboard RAID controller.  If you lose the motherboard, you lose your data--simple.  If this is a simple RAID1 mirror, then both disks should have the same data.  If it is software RAID, then it could be *mdadm* or it could be some proprietary, VXware or something else.  Regardless, 6 years ago, *mdadm* was probably not mature enough for production use, so it's doubtful that was used for RAID.  

Take the NAS apart and repair it.  It may only be a few 25-cent capacitors.  I just repaired a $3k, 12-channel whole house sound system using $8 worth of parts--2006 vintage.  There are a lot of bad capacitors out there.

It's possible that the power section of the NAS has enough power to give you a green status light, but not enough power to spin the drives.  Take one drive out and hope it boots.  If so, back up your data.

---

