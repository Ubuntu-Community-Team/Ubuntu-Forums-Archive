---
title: "Recovering RAID disk from windows"
date: 2017-09-19
forum: General Help
---

### Post by rxkmir05 on 2017-09-19
Hello, 
I'm trying to recover a raid disk, I was looking around for some answers and I only found a few. Here are some info regarding my progress.

Drive info:

```

/mnt$ sudo fdisk -l
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000390b6


Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048   1026047   1024000   500M  7 HPFS/NTFS/exFAT
/dev/sda2         1026048 488386559 487360512 232.4G  7 HPFS/NTFS/exFAT
/dev/sda3       488386560 966901759 478515200 228.2G 83 Linux
/dev/sda4       966903806 976771071   9867266   4.7G  5 Extended
/dev/sda5       966903808 976771071   9867264   4.7G 82 Linux swap / Solaris




Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5b067028


Device     Boot Start        End    Sectors Size Id Type
/dev/sdb1           1 4294967295 4294967295   2T ee GPT

```

Where sdb and sdb1 are my target disks
I also ran gdisk and this is the output:

```
/mnt$ sudo gdisk /dev/sdb 
GPT fdisk (gdisk) version 1.0.1


Warning! Disk size is smaller than the main header indicates! Loading
secondary header from the last sector of the disk! You should use 'v' to
verify disk integrity, and perhaps options on the experts' menu to repair
the disk.
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.


Warning! One or more CRCs don't match. You should repair the disk!


Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged


****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************


Command (? for help): 



```

I would like to know how I can mount and recover the files from the disk. Any help would be appreciated.


Thanks!

---

### Post by TheFu on 2017-09-19
Nothing in what you've posted says "RAID".

BTW, sdb1 is the first partition on the disk, sdb.  They overlap with sdb being the entire disk device.

What type of RAID did you use?  Possible answers are:
* fakeRAID
* SW-RAID
* HW-RAID

There are no good reasons to use fakeRAID.  That is the RAID provided by the motherboard.  It has all the limitations of HW-RAID, without all the speed and flexibility of SW-RAID.

Linux SW-RAID isn't available under Windows.
HW-RAID might be, but only if the exact version of the drivers is used for both Windows and Linux AND if Linux can access the underlying file system.  That isn't usually possible, since anyone using RAID would likely use xfs or some other modern file system.  You'll need to know the file system used.

OTOH, if you want to get the data off, you can access RAID data from a live Linux boot, with some manual configuration. But it is impossible to help without the requested information.

---

