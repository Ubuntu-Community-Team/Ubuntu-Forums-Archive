---
title: "Directory creation permission by Backup onto separate partition"
date: 2017-02-23
forum: General Help
---

### Post by JamButty on 2017-02-23
Have seen a couple of similar threads but not quite the same. After reloading the squirrel onto the boot partition, the backup (standard Ubuntu issue) program no longer has access to create directories on my backups partition. Elsewhere I read that partitions do not have owners, so I can't correct with CHOWN, but have to do something with the ownership of the mount point. I don't follow how to do that. The partition mounts on boot, I have read access (restore from there was no problem), but I cannot write new backup data.
If nothing else, I assume I can just format the partition to regain ownership, but is there a less extreme method?
thanks.

disk/partition info in case that helps (partition in question is /dev/sda8):
```
max@max-Inspiron-3847:~$ sudo parted -l
[sudo] password for max: 
Model: ATA ST2000DM001-1ER1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  525MB   524MB   fat32           EFI system partition          boot, esp
 2      525MB   660MB   134MB                   Microsoft reserved partition  msftres
 3      660MB   1009GB  1008GB  ntfs            Basic data partition          msftdata
 6      1009GB  1870GB  861GB   ext4
 8      1870GB  1974GB  105GB   ext4            Backups
 7      1974GB  1987GB  12.8GB  linux-swap(v1)
 4      1987GB  1988GB  472MB   ntfs                                          hidden, diag
 5      1988GB  2000GB  12.8GB  ntfs                                          hidden, diag


max@max-Inspiron-3847:~$ 
==========
max@max-Inspiron-3847:~$ sudo fdisk -lu
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sector

Device          Start        End    Sectors   Size Type
/dev/sda1        2048    1026047    1024000   500M EFI System
/dev/sda2     1026048    1288191     262144   128M Microsoft reserved
/dev/sda3     1288192 1970010111 1968721920 938.8G Microsoft basic data
/dev/sda4  3881201664 3882123263     921600   450M Windows recovery environment
/dev/sda5  3882123264 3907028991   24905728  11.9G Windows recovery environment
/dev/sda6  1970010112 3651407871 1681397760 801.8G Linux filesystem
/dev/sda7  3856207872 3881201663   24993792  11.9G Linux swap
/dev/sda8  3651407872 3856207871  204800000  97.7G Linux filesystem

Partition table entries are not in disk order.


max@max-Inspiron-3847:~$ 
----------------
max@max-Inspiron-3847:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=300b387f-16e0-4408-b913-4fef9f9666ce /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=EC12-1A71  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda7 during installation
UUID=82d1c7a8-fd75-4ae9-b322-e07e781cbcd7 none            swap    sw              0       0
max@max-Inspiron-3847:~$ 
==============
max@max-Inspiron-3847:~$ sudo blkid -c /dev/null -o list
[sudo] password for max: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  vfat    ESP      /boot/efi      EC12-1A71
/dev/sda2                   (not mounted)  
/dev/sda3  ntfs    OS       (not mounted)  608E3C548E3C24C6
/dev/sda4  ntfs    WINRETOOLS (not mounted) 62C87289C8725AED
/dev/sda5  ntfs    Image    (not mounted)  1C9073369073160C
/dev/sda6  ext4             /              300b387f-16e0-4408-b913-4fef9f9666ce
/dev/sda7  swap             [SWAP]         82d1c7a8-fd75-4ae9-b322-e07e781cbcd7
/dev/sda8  ext4    Backups  /media/max/Backups 69c75e7d-1011-484f-ad4b-ad1a0582acb9
max@max-Inspiron-3847:~$ 


```

---

### Post by yancek on 2017-02-23
What is the mount point for sda8?  Use the command:  ls -l /path/to/mountpoint to get the ownership and permissions.  Copying 'from' a partition only requires read permissions, writing to it obviously requires 'write' permissions.

---

### Post by JamButty on 2017-02-23
This article is partition permissions for dummies. Everything is ok now.
[https://itsfoss.com/set-write-permission-ext4-partition-ubuntu-linux/](https://itsfoss.com/set-write-permission-ext4-partition-ubuntu-linux/)

---

