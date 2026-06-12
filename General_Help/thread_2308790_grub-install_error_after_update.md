---
title: "grub-install error after update"
date: 2016-01-05
forum: General Help
---

### Post by Sven_Richter on 2016-01-05
Hi, 

Yesterday I did an apt-get update on my machine:

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty

During the update process I got an error saying that grub-install failed. Also the update stopped.
Now when I manually try to run grub-install I get the same error:

grub-install /dev/sdb
Installing for i386-pc platform.
grub-install: error: disk `mduuid/32f3800c32f8e591df70a045db28f609' not found.

This is what fdisk -l says:
fdisk -l
WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
256 heads, 63 sectors/track, 363376 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.


Disk /dev/md2: 2991.3 GB, 2991329640448 bytes
2 heads, 4 sectors/track, 730305088 cylinders, total 5842440704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table


Disk /dev/md0: 8585 MB, 8585674752 bytes
2 heads, 4 sectors/track, 2096112 cylinders, total 16768896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table


Disk /dev/md1: 536 MB, 536543232 bytes
2 heads, 4 sectors/track, 130992 cylinders, total 1047936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

There are two disks running a software raid. This is the output of mdadm:

mdadm --detail --scan
ARRAY /dev/md/2 metadata=1.2 name=rescue:2 UUID=49425383:18f73adb:6ebb09e6:fc69e14a
ARRAY /dev/md/0 metadata=1.2 name=rescue:0 UUID=861ecfae:2c015de6:229d0894:82819cc0
ARRAY /dev/md/1 metadata=1.2 name=rescue:1 UUID=32f3800c:32f8e591:df70a045:db28f609


Which  fits to the content of my mdadm.conf:
cat /etc/mdadm/mdadm.conf

CREATE owner=root group=disk mode=0660 auto=yes

HOMEHOST <system>

MAILADDR root

ARRAY /dev/md/0 metadata=1.2 UUID=861ecfae:2c015de6:229d0894:82819cc0 name=rescue:0
ARRAY /dev/md/1 metadata=1.2 UUID=32f3800c:32f8e591:df70a045:db28f609 name=rescue:1
ARRAY /dev/md/2 metadata=1.2 UUID=49425383:18f73adb:6ebb09e6:fc69e14a name=rescue:2

Any ideas what is going on here?

Thanks, 
Sven

---

