---
title: "Can't make a live persistent USB Ubuntu"
date: 2008-02-10
forum: General Help
---

### Post by galvao on 2008-02-10
Greetings.

I've followed the instructions of [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) to make a Persistent Gutsy on my 2Gb pen drive. I've followed exactly all the steps in there, but when I try to boot from the pen drive all I get is "Boot error".

Can someone please help me?

This is the log of my terminal (everything I've done following the steps in there):

```
galvao@galvao-desktop ~> mount
/dev/sdb5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sdb6 on /home type ext3 (rw)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdc2 on /media/casper-rw type ext2 (rw,nosuid,nodev)
/dev/sdc1 on /media/ubuntu type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,user=galvao)
galvao@galvao-desktop ~> sudo umount /dev/sdc1
[sudo] password for galvao:
Sorry, try again.
[sudo] password for galvao:
galvao@galvao-desktop ~> sudo umount /dev/sdc2
galvao@galvao-desktop ~> sudo fdisk /dev/sdc

The number of cylinders for this disk is set to 7624.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sdc: 1998 MB, 1998585856 bytes
16 heads, 32 sectors/track, 7624 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2862      732656    6  FAT16
/dev/sdc2            2863        7624     1219072   83  Linux

Command (m for help): d
Partition number (1-4): 1

Command (m for help): p

Disk /dev/sdc: 1998 MB, 1998585856 bytes
16 heads, 32 sectors/track, 7624 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2            2863        7624     1219072   83  Linux

Command (m for help): d
Selected partition 2

Command (m for help): p

Disk /dev/sdc: 1998 MB, 1998585856 bytes
16 heads, 32 sectors/track, 7624 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-7624, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-7624, default 7624): +750M

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 6
Changed system type of partition 1 to 6 (FAT16)

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 2
First cylinder (2863-7624, default 2863): 
Using default value 2863
Last cylinder or +size or +sizeM or +sizeK (2863-7624, default 7624): 
Using default value 7624

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.

WARNING: If you have created or modified any DOS 6.x
partitions, please see the fdisk manual page for additional
information.
Syncing disks.
galvao@galvao-desktop ~> sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e3e1e3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7298    58621153+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06930692

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3835    30804606    7  HPFS/NTFS
/dev/sdb2            6376       19214   103129267+   f  W95 Ext'd (LBA)
/dev/sdb3           19215       19452     1911735   82  Linux swap / Solaris
/dev/sdb5            6376        8880    20121381   83  Linux
/dev/sdb6            8881       19214    83007823+  83  Linux

Disk /dev/sdc: 1998 MB, 1998585856 bytes
16 heads, 32 sectors/track, 7624 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2862      732656    6  FAT16
/dev/sdc2            2863        7624     1219072   83  Linux
galvao@galvao-desktop ~> sudo umount /dev/sdc1
galvao@galvao-desktop ~> sudo umount /dev/sdc2
galvao@galvao-desktop ~> sudo mkfs.vfat -F 32 -n ubuntu /dev/sdc1
mkfs.vfat 2.11 (12 Mar 2005)
galvao@galvao-desktop ~> sudo mkfs.ext2 -b 4096 -L casper-rw /dev/sdc2
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=casper-rw
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
152640 inodes, 304768 blocks
15238 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=314572800
10 block groups
32768 blocks per group, 32768 fragments per group
15264 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912

Writing inode tables: done                            
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 32 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
galvao@galvao-desktop ~> cd /media/cdrom0
galvao@galvao-desktop /m/cdrom0> ls
autorun.inf*  casper/    dists/    isolinux/   pics/  preseed/   README.diskdefines  start.exe*  ubuntu@      wubi-cdboot.exe
bin/          disctree/  install/  md5sum.txt  pool/  programs/  start.bmp*          start.ini*  ubuntu.ico*
galvao@galvao-desktop /m/cdrom0> cp -rf casper disctree dists install pics pool preseed .disk /media/ubuntu
cp: cannot create symbolic link `/media/ubuntu/dists/stable': Operation not permitted
cp: cannot create symbolic link `/media/ubuntu/dists/unstable': Operation not permitted
galvao@galvao-desktop /m/cdrom0> cp isolinux/* md5sum.txt README.diskdefines ubuntu.ico /media/ubuntu
galvao@galvao-desktop /m/cdrom0> cp casper/vmlinuz casper/initrd.gz install/mt86plus /media/ubuntu
galvao@galvao-desktop /m/cdrom0> cd /media/ubuntu/
galvao@galvao-desktop /m/ubuntu> mv isolinux.cfg syslinux.cfg
galvao@galvao-desktop /m/ubuntu> gedit syslinux.cfg 
galvao@galvao-desktop /m/ubuntu> cd ~
galvao@galvao-desktop ~> sudo umount /dev/sdc1
galvao@galvao-desktop ~> syslinux -f /dev/sdc1
galvao@galvao-desktop ~> eject /dev/sdc
umount: /media/casper-rw is not in the fstab (and you are not root)
eject: unmount of `/media/casper-rw' failed
galvao@galvao-desktop ~> sudo eject /dev/sdc
```and my pendrive's syslinux.cfg ended up exactly as the one in that tutorial.

So, whathave I missed??? Someone at freenode's #ubuntu told me that I should do "sudo syslinux -f /dev/sdc1", but that didn't solved. Tried with "-sf", without any options....

I'm stuck!

TIA,

---

### Post by PhilOSparta on 2008-03-10
Same problem here after spending a solid 8 hours working on this.
However, I tried the USB pen drive on my Inspiron 8600 and it worked fine.
It fails on my new Dell 530N Ubuntu preloaded desktop.

I have the boot order set to Removable, CD-ROM, Hard Drive in that order and that seems to be set up correctly.

On power up there are one or two lines of text that flash for about 10th of a second prior to  "Boot error".  Much too fast to read.

Knowing that the Pen Drive is okay and bootable, how does one prove that the PC itself can be booted from a USB port?  What is the bare bones setup on the USB drive to generate a message on the monitor that the system has accessed the MBR of the pen drive?

That would be a step in determining what's wrong.](*,)

---

### Post by parsimony on 2008-04-21
> **PhilOSparta said:**
> 
Same problem here after spending a solid 8 hours working on this.
However, I tried the USB pen drive on my Inspiron 8600 and it worked fine.
It fails on my new Dell 530N Ubuntu preloaded desktop.

On power up there are one or two lines of text that flash for about 10th of a second prior to  "Boot error". 

Thanks! Same problem here after spending days on this.

So it doesn't work on my Dell Dtop 530 - but it does on my Dell 1520!

I thought the "Boot Error" was a problem with the UDB drive - but its obviously the booting computer.

So... a problem with the Dell 530

:)

---

### Post by neutrl on 2008-04-27
anyone  ever find a resolution to this issue?

I can't get my 530 to boot anyting off usb, but my usb pendrives will boot just about another other machine including my sister's four year old 2400

---

### Post by neutrl on 2008-05-01
> **neutrl said:**
> anyone  ever find a resolution to this issue?

I can't get my 530 to boot anyting off usb, but my usb pendrives will boot just about another other machine including my sister's four year old 2400


I got mine working on a Dell 530 if anyone cares. :guitar:

Just flashed the bios with the newest, played around with some settings in bios and viola

---

