---
title: "Unable to mount: NTFS signature is missing"
date: 2013-07-07
forum: General Help
---

### Post by Dreadslayer on 2013-07-07
Hi there

I was about to migrate my system (and therefore data) from a "Windows Server 2008 R2" to a "Ubuntu Server 12.04.2" installation. So i chucked all of my data two times on two disks (basic NTFS Primary Partition).

After ejecting the drives and starting up Ubuntu Server, i tried to mount them with:

```
$ sudo mount -t ntfs /dev/sda1 /media/wd3a
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

The same happens when trying to mount the second disk/partition "/dev/sdb1". I also already checked both with "chkdsd /f", no error was found.

Help/suggestions would be much appreciated!

Additional information:

```
$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
256 heads, 63 sectors/track, 363376 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
256 heads, 63 sectors/track, 363376 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

...
```

```
morrow@server:~$ sudo parted -l
Model: ATA WDC WD30EFRX-68A (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
 2      135MB   3001GB  3000GB  ntfs         Basic data partition


Model: ATA WDC WD30EFRX-68A (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
 2      135MB   3001GB  3000GB  ntfs         Basic data partition
```

```
$ sudo ntfsfix /dev/sda
Mounting volume...
NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
Unrecoverable error
Volume is corrupt. You should run chkdsk.
```

---

### Post by steeldriver on 2013-07-07
it looks like sda**1** / sdb**1** are the msftres partitions, no? have you tried mounting sda**2** / sdb**2**

---

### Post by Dreadslayer on 2013-07-07
Well, this certainly worked, thanks... I'm wondering, why doesn't "fdisk -l" list the actual partition?

---

### Post by steeldriver on 2013-07-07
well like it says, fdisk doesn't really understand GPT partition tables

---

