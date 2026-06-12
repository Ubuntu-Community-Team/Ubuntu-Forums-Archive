---
title: "Mount the right disk on startup"
date: 2008-06-09
forum: General Help
---

### Post by OA-5599 on 2008-06-09
How can I make my 250GB Ext3 Disk mount on startup?
Sometimes it is already mounted on startup, sometimes my 80GB NTFS disk is mounted instead, sometimes nothing is mounted. I have to type 
sudo mount /dev/sdc1 /media/media
and sometimes
sudo mount /dev/sda1 /media/media
to get the right results.
I have installed ubuntu studio 8.04 but I already had this problem at ubuntu 8.04.

---

### Post by kpkeerthi on 2008-06-09
To have disks/partitions mounted at startup, you need to add them to /etc/fstab.

Can you post the outputs of below commands?
```
cat /etc/fstab
```
```
sudo fdisk -l
```

And let me know, from the output of **fdisk**, which ones you want to mount at startup.

---

### Post by sisco311 on 2008-06-09
post the output from:

```
mount
``````
sudo fdisk -l
``````
cat /etc/fstab
``````
sudo blkid
```

---

### Post by OA-5599 on 2008-06-09
> **sisco311 said:**
> ```
mount
```

```
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-18-rt/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdc1 on /media/media type ext3 (rw)
```

> **sisco311 said:**
> ```
sudo fdisk -l
```

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd10b311d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096    7  HPFS/NTFS
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc457b704

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6994    56179273+  83  Linux
/dev/sdb2            6995        7297     2433847+   5  Extended
/dev/sdb5            6995        7297     2433816   82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00b2dbff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      484518   244197040+  83  Linux
```

> **sisco311 said:**
> ```
cat /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=ed80c262-e7da-4567-9e53-a8c37f11ad64 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=302cd89d-6e56-4a70-bace-0195c7b9f01f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

> **sisco311 said:**
> ```
sudo blkid
```

```
/dev/sda1: UUID="E4105F34105F0D44" TYPE="ntfs" 
/dev/sdb1: UUID="ed80c262-e7da-4567-9e53-a8c37f11ad64" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="302cd89d-6e56-4a70-bace-0195c7b9f01f" 
/dev/sdc1: UUID="fe174b40-001f-4c0f-9e37-910df1e328af" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda5: TYPE="swap" UUID="f23cc123-550c-47cb-bfec-cbd0fd2549b6"
```

---

### Post by sisco311 on 2008-06-09
To mount the ext3 partition add this line to the fstab:
> UUID=fe174b40-001f-4c0f-9e37-910df1e328af /media/media ext3 relatime,defaults 0 2The device name(sda, sdb, sdc ...) can alter after a reboot.
The uuid of a partition is an unique identifier. 
Mounting the partition by uuid will solve your problem.

To edit the fstab:
```
gksu gedit /etc/fstab
```

EDIT:
from fdisk -l:
> [FONT=monospace]
[/FONT]**Disk /dev/sdc: 250.0 GB, 250059350016 bytes**[FONT=monospace]
[/FONT]16 heads, 63 sectors/track, 484521 cylinders[FONT=monospace]
[/FONT]Units = cylinders of 1008 * 512 = 516096 bytes[FONT=monospace]
[/FONT]Disk identifier: 0x00b2dbff   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      484518   244197040+  83  Linux[FONT=monospace]
sdc is the 250GB disk

from blkid:
> [/FONT]/dev/sdc1: UUID="fe174b40-001f-4c0f-9e37-910df1e328af" TYPE="ext3" SEC_TYPE="ext2" 
[FONT=monospace]the uuid of the partition is: [/FONT]fe174b40-001f-4c0f-9e37-910df1e328af

---

### Post by OA-5599 on 2008-06-09
Thank you

---

