---
title: "'drivemap not found' - Dual booting problem Windows 8.1 and Ubuntu on Lenovo"
date: 2014-01-26
forum: General Help
---

### Post by Biro_Denes on 2014-01-26
[INDENT] 					Hi Everyone, 

I try to do a dual boot (actually a trio (win7 - win8.1 - ubuntu) on a lenovo z500.
Ubuntu boots with grub but the two windows can't (drivemap can't  found).
It's MBR partition since windows couldn't install on gpt style partition  
Please help me find a solution - maybe it's start all over or forget dual boot or forget windows 8.1.

here are my lists:
root@dns-Lenovo-IdeaPad-Z500:~# sudo parted -l
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  200MB   199MB   primary   fat32           boot
 4      201MB   440GB   440GB   extended                  lba
 6      201MB   22.7GB  22.5GB  logical   ext4
 7      22.7GB  27.5GB  4799MB  logical   linux-swap(v1)
 8      27.5GB  215GB   188GB   logical   ext4
 5      215GB   440GB   225GB   logical   ntfs
 2      440GB   661GB   220GB   primary   ntfs
 3      661GB   1000GB  340GB   primary   ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

root@dns-Lenovo-IdeaPad-Z500:~# sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x09806300

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      391167      194560    b  W95 FAT32
/dev/sda2       860152230  1290228344   215038057+   7  HPFS/NTFS/exFAT
Partition 2 does not start on physical sector boundary.
/dev/sda3      1290228345  1953520064   331645860    7  HPFS/NTFS/exFAT
Partition 3 does not start on physical sector boundary.
/dev/sda4          393214   860151807   429879297    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5       419926016   860151807   220112896    7  HPFS/NTFS/exFAT
/dev/sda6          393216    44298239    21952512   83  Linux
/dev/sda7        44300288    53673983     4686848   82  Linux swap / Solaris
/dev/sda8        53676032   419923967   183123968   83  Linux

Partition table entries are not in disk order 				
[/INDENT]

---

### Post by coffeecat on 2014-01-26
Duplicate of:

[http://ubuntuforums.org/showthread.php?t=2201852](http://ubuntuforums.org/showthread.php?t=2201852)

Thread closed.

---

