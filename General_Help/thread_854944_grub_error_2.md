---
title: "grub error 2"
date: 2008-07-10
forum: General Help
---

### Post by rmvg on 2008-07-10
Here is my newest mess

Using fdisk I have created 4 identical partitions on 2 identical disks they are all primary partitions. see fdisk -l and mount commands below. Note i have only mounted / and /boot think that is all i need right?

/boot
/
/swap
/a large lvm

I have dumped ubuntu onto this setup from a disaster recovery system. However the new system will not boot i am pretty sure this has to do with grub. 

I have read several howtos about grub and none of them have worked to get my system to boot please help

Disk /dev/md2 doesn't contain a valid partition table
[root@rescue ~]# mount
none on / type tmpfs (rw,noatime)
none on /proc type proc (rw)
usbfs on /proc/bus/usb type usbfs (rw)
sysfs on /sys type sysfs (rw)
none on /dev/cpuset type cpuset (rw)
none on /dev/pts type devpts (rw,gid=5,mode=620)
none on /dev/shm type tmpfs (rw)
/dev/md/1 on /mnt/boot type ext2 (rw)
/dev/md/2 on /mnt type ext3 (rw)


[root@rescue ~]# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c375105

Device Boot Start End Blocks Id System
/dev/sda1 * 1 125 1004031 fd Linux raid autodetect
/dev/sda2 126 250 1004062+ fd Linux raid autodetect
/dev/sda3 251 749 4008217+ fd Linux raid autodetect
/dev/sda4 750 60801 482367690 fd Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd35ca048

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 125 1004031 fd Linux raid autodetect
/dev/sdb2 126 250 1004062+ fd Linux raid autodetect
/dev/sdb3 251 749 4008217+ fd Linux raid autodetect
/dev/sdb4 750 60801 482367690 fd Linux raid autodetect

Disk /dev/md1: 1027 MB, 1027997696 bytes
2 heads, 4 sectors/track, 250976 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

---

