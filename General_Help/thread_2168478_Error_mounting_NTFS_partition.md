---
title: "Error mounting NTFS partition"
date: 2013-08-18
forum: General Help
---

### Post by galih2 on 2013-08-18
I can't mount my partition which is /dev/sda5/ when I try to access my partition it says > Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda5 on /media/data. Here's the output of the fstab:

```
# /etc/fstab: static file system information.#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>


proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda4 :
UUID=b290d17a-8936-4c10-988c-f9fe1faeb31d	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=2CC0F55EC0F52EA8	/media/SYSTEM	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda5 :
UUID=EE643DE6643DB1E7	/media/data	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-8	0	0
#Entry for /dev/sda2 :
UUID=78D84BF2D84BACE6	/media/sda2	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
UUID=706ba526-df7d-4be3-8368-36d27abb78d9	none	swap	sw	0	0



```

and here's the output when I do > [COLOR=#000000][FONT=Ubuntu Mono]sudo fdisk -l[/FONT][/COLOR]
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x796ffdc4


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2   *      409600    70293114    34941757+   7  HPFS/NTFS/exFAT
/dev/sda3        70293502   465416191   197561345    f  W95 Ext'd (LBA)
/dev/sda4       465416192   488396799    11490304   83  Linux
/dev/sda5        71319552   465416191   197048320    7  HPFS/NTFS/exFAT
/dev/sda6        70293504    71317503      512000   82  Linux swap / Solaris


Partition table entries are not in disk order


Disk /dev/sdb: 1948 MB, 1948254208 bytes
256 heads, 63 sectors/track, 235 cylinders, total 3805184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0e362c6b


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     3805183     1901568    6  FAT16



```

Please help

---

### Post by galih2 on 2013-08-18
Solved by mounting it via Gparted

---

