---
title: "Mounting WD MyBook External HD"
date: 2008-03-19
forum: General Help
---

### Post by sstusick on 2008-03-19
I just bought a WD MyBook and I can't mount it. I've searched through the forums and tried to follow the steps but no luck and am lost at this point and just about out of patience.

I want to mount this drive and be able to USE it and have it mount auto upon bootup.


> stu@stu-laptop:~$ sudo lshw -C disk
  *-disk
       description: SCSI Disk
       product: HTS541010G9SA00
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: MBZO
       serial: MP2ZM4X0HVMRNR
       size: 93GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ-841S
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.50
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       product: 2500JB External
       vendor: WD
       physical id: 0.0.0
       bus info: scsi@16:0.0.0
       logical name: /dev/sde
       version: 0107
       size: 232GB
       capabilities: partitioned partitioned:dos


> 
stu@stu-laptop:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06d706d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         122      979933+  82  Linux swap / Solaris
/dev/sda2             123        3188    24627645   83  Linux
/dev/sda3   *        3189        8286    40949685    b  W95 FAT32
/dev/sda4            8287       12161    31125937+   b  W95 FAT32

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30401   244196001    b  W95 FAT32


> stu@stu-laptop:~$ kdesudo kate /etc/mtab

/dev/sda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
/dev/sda3 /media/sda3 vfat rw,utf8,umask=007,gid=46 0 0
/dev/sda4 /media/sda4 vfat rw,utf8,umask=007,gid=46 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

> stu@stu-laptop:~$ kdesudo kate /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=8e71183b-a7a9-4317-9154-7efc5ebc7b71 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=9211-E65B  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=0CA1-90D0  /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=c0012f32-f5ab-4642-9aa9-2fc9a703098a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

As you can see I've tried some things that didn't work, and screwed up the mounting process because nothing else will mount, cameras, flash drives, etc.

Any help would be appreciated.

---

### Post by amd-64 on 2008-03-19
I have one of those,  WD 120Gb, and it works flawlessly. The only time it did not work was when i used a longer USB cable (3-4ft). I could not mount it until I switched back to the 6 inch cable. 

With the short usb cable connected, try to mount manually using

sudo mkdir /media/sde1
sudo mount -t vfat  /dev/sde1 /media/sde1
df -h

---

### Post by sstusick on 2008-03-20
I only have a 6 foot USB cable. 

I tried sudo mount -t vfat /dev/sde1 /media/sde1

and got: 
```
stu@stu-laptop:~$ sudo mount -t vfat /dev/sde1 /media/sde1
mount: wrong fs type, bad option, bad superblock on /dev/sde1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so 
```

---

### Post by badmedic on 2008-03-20
I have a 750 GB WD MyBook that I bought a few months ago. I can't remember if it mounted from the start, but I have a sneaking suspicion it didn't. I do know that immediately formatted it using gparted and then it mounted right up.

I basically followed steps 1 and 2 from this guide: [http://www.mattcutts.com/blog/format-external-drive-for-linux/](http://www.mattcutts.com/blog/format-external-drive-for-linux/)

---

### Post by sstusick on 2008-03-20
Thanks for the link, I'll check it out.

---

### Post by sstusick on 2008-03-20
Bump - anyone?

---

### Post by amd-64 on 2008-03-20
If you can see it in gparted or qtparted, I would agree that you should first wipe it clean, and create one or more partitions. Mine now has fat and ext3 partitions.

---

