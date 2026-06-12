---
title: "Having Problems Formating/Partitioning/Mounting Drive"
date: 2007-12-18
forum: General Help
---

### Post by bertsisterwanda on 2007-12-18
I am pretty stuck trying to get one of my disc arrays to mount, i am running ubuntu 7.10 server edition.
I need a good step by step guide to get the drive formated through to mounted. The drive is to be used for all my web site hosting.

The drive in question is Disk /dev/cciss/c0d1: 599.9 GB, 599990482944 bytes
i want it mounted at /media/hda1

Result of sudo fdisk -l
[HTML]
Disk /dev/cciss/c0d0: 72.8 GB, 72833679360 bytes
255 heads, 63 sectors/track, 8854 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c6e8c6e

           Device Boot      Start         End      Blocks   Id  System
/dev/cciss/c0d0p1   *           1        8488    68179828+  83  Linux
/dev/cciss/c0d0p2            8489        8854     2939895    5  Extended
/dev/cciss/c0d0p5            8489        8854     2939863+  82  Linux swap / Solaris

Disk /dev/cciss/c0d1: 599.9 GB, 599990482944 bytes
255 heads, 32 sectors/track, 143609 cylinders
Units = cylinders of 8160 * 512 = 4177920 bytes
Disk identifier: 0x39a087d4

           Device Boot      Start         End      Blocks   Id  System
/dev/cciss/c0d1p1               1      143609   585924704   83  Linux
[/HTML]
Runing mount-a
[HTML]
mount: wrong fs type, bad option, bad superblock on /dev/cciss/c0d1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/HTML]
My /etc/fstab looks like
[HTML]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/cciss/c0d0p1
UUID=f130a698-3ea0-4522-9fd4-cc6e83448c91 /               ext3    defaults,errors=remount-ro 0       1
# /dev/cciss/c0d0p5
UUID=70e6a8d1-d6fc-4bbb-897c-3aec8da60d28 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 1    1
/dev/cciss/c0d1 /media/hda1            ext3 defaults 1   1
[/HTML]

any help, guidance will be appreciated

---

### Post by starfry on 2007-12-18
Hi, have you made a filesystem?

Assuming you want to mount /dev/cciss/c0d1 on /media/hda1, and it's a new disk:

I assume you have made a Linux partition using fdisk because of this:

Disk /dev/cciss/c0d1: 599.9 GB, 599990482944 bytes
           Device Boot      Start         End      Blocks   Id  System
/dev/cciss/c0d1p1               1      143609   585924704   83  Linux

You need to make an ext3 partition on it:

$ mke2fs -j /dev/cciss/c0d1p1

(that may require a sudo as well)

Then, in /etc/fstab:

dev/cciss/c0d1p1 /media/hda1            ext3 defaults 1   1

(note the addition of p1 to what you had).

Just in case, make sure /media/hda1 mount point exists. If not:

$ sudo mkdir /media/hda1

Then, as if by magic:

sudo mount /media/hda1

Good Luck!

---

### Post by geirha on 2007-12-18
The last two fields should be 0 2 instead of 1 1, so ```
/dev/cciss/c0d1p1 /media/hda1 ext3 defaults 0 2
``` would be the correct line in fstab. What those fields mean are explained in fstab's man-page ```
man fstab
```

---

### Post by bertsisterwanda on 2007-12-18
Thanks Guys

I dont really get why i had to add p1, but the mount seems to appear like something is mounted to the media/hda1    is there anything i can do to check the correct drive is mounted, maybe get the size in bytes of the drive?


[HTML]/dev/cciss/c0d0p1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/cciss/c0d1p1 on /media/hda1 type ext3 (rw)
[/HTML]

---

### Post by starfry on 2007-12-18
You need to add the p1 because you are mounting a partition.

/dev/cciss/c0d1 is what is known as the "raw device": it's the whole disk and is what you chop into partitions. Each partition will be suffixed p1, p2, etc. You have to have a partition, even if it is the whole disk, hence the /dev/cciss/c0d1p1.

To get the size of the drive (partition) you can use

df -k /media/hda1

It won't be exact because there are overheads around the filesystem but it will be in the right ball-park so you know you're on the right disk.

---

