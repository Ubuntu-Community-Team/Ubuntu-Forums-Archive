---
title: "Unable to mount USB stick"
date: 2017-09-04
forum: General Help
---

### Post by satimis on 2017-09-04
Hi all,

Ubuntu 16.04

&#10219; sudo fdisk -l```

.....
Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048    999423    997376   487M 83 Linux
/dev/sda2       1001470 250068991 249067522 118.8G  5 Extended
/dev/sda5       1001472 250068991 249067520 118.8G 8e Linux LVM
.....
Disk /dev/sdb: 59.5 GiB, 63864569856 bytes, 124735488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start       End   Sectors  Size Id Type
/dev/sdb1       32768 124735487 124702720 59.5G  7 HPFS/NTFS/exFAT

```


&#10219; sudo mount -t ext4 /dev/sdb1 /media/satimis```

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

&#10219; sudo mount -t exfat /dev/sdb1 /media/satimis```

FUSE exfat 1.2.3
WARN: volume was not unmounted cleanly.
ERROR: fsync failed: Remote I/O error.

```

&#10219; sudo umount /dev/sdb1```

umount: /dev/sdb1: not mounted

```

&#10219; sudo umount /dev/sdb```

umount: /dev/sdb: not mounted

```

&#10219; sudo umount /media/satimis```

umount: /media/satimis: not mounted

```

&#10219; apt-cache policy exfat-fuse exfat-utils```

exfat-fuse:
  Installed: 1.2.3-1
  Candidate: 1.2.3-1
  Version table:
 *** 1.2.3-1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status
exfat-utils:
  Installed: 1.2.3-1
  Candidate: 1.2.3-1
  Version table:
 *** 1.2.3-1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status

```
They are already installed

Please help.  Thanks


Edit
====
Sorry, I forgot to format the USB stick.

Perform following steps;

&#10219; sudo mkfs.ext4 /dev/sdb```

mke2fs 1.42.13 (17-May-2015)
Found a dos partition table in /dev/sdb
Proceed anyway? (y,n) y
Creating filesystem with 15591936 4k blocks and 3899392 inodes
Filesystem UUID: 348cf5c1-8e6f-41da-af97-7c26bedaaae1
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information:        
done

```

&#10219; sudo mount -t ext4 /dev/sdb /media/satimis
Now it works

&#10219; sudo fdisk -l```

.....
Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048    999423    997376   487M 83 Linux
/dev/sda2       1001470 250068991 249067522 118.8G  5 Extended
/dev/sda5       1001472 250068991 249067520 118.8G 8e Linux LVM
....
Disk /dev/sdb: 59.5 GiB, 63864569856 bytes, 124735488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```


Regards
satimis

---

