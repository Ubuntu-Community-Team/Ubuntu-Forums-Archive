---
title: "mdadm array gone missing"
date: 2017-01-04
forum: General Help
---

### Post by ilemur on 2017-01-04
Updated the system with errors of out of disk space on /boot.
So ran autoremove to free up. During this run i've seen some messages complaining that mdadm.conf is used by other kernel or something like that (didn't write it down).
Aftwerwards experienced a power outage and as such my raid0 array is gone missing. Is there anything that can be done to bring it back? The array consisted of sdb and sdc

```
~$ sudo mdadm --detail --scan --verbose
~$

```
```
:~$ sudo mdadm --detail /dev/sdb1
mdadm: /dev/sdb1 does not appear to be an md device
ilemur@walle:~$ sudo mdadm --detail /dev/sdc1
mdadm: /dev/sdc1 does not appear to be an md device

```


```
~$ sudo parted /dev/sdb print
Model: ATA TOSHIBA DT01ACA2 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  2000GB  2000GB               primary


~$ sudo parted /dev/sdc print
Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  2000GB  2000GB               primary

```

~$ cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/walle--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=b782f115-936a-4f6a-9033-51f5a2741079 /boot           ext2    defaults        0       2
/dev/md0	/torrents	auto	defaults,noatime,nodiratime	0	0
/dev/mapper/walle--vg-swap_1 none            swap    sw              0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root

```
```

sudo cat /proc/mdstat
Personalities : linear multipath raid0 raid1 raid6 raid5 raid4 raid10
unused devices: none

```

---

