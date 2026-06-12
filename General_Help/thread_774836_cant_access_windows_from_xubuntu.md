---
title: "cant access windows from xubuntu"
date: 2008-04-29
forum: General Help
---

### Post by richardy on 2008-04-29
Hi,
I have just installed Hardy and have noticed that i can no longer access windows or any other operating system from xubuntu. I was able to do this using previous versions and is a very useful feature. How do i go about correcting this. Any help would be much appreciated.

Cheers.

---

### Post by eriqjaffe on 2008-04-29
Are you trying to access Windows partitions on your local machine?  Or is this over a network?

---

### Post by richardy on 2008-04-29
> **eriqjaffe said:**
> Are you trying to access Windows partitions on your local machine?  Or is this over a network?

Just the windows partitions on my machine. I have windows dual booted with Xubuntu and want to be able to access windows. I used to have Xubuntu (Gutsy) dual booted with windows and mepis and was able to access both windows and mepis from Xubuntu.

Cheers.

---

### Post by Zorael on 2008-04-29
Could you post the terminal output of the following command?
```
$ sudo fdisk -l
```

And the contents of **/etc/fstab** and **/etc/mtab**?

---

### Post by richardy on 2008-04-30
Hi Zorael,
Thanks for replying.
 
Output from sudo fdisk -l:
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd53d826f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   1b  Hidden W95 FAT32
/dev/sda2   *         244        3019    22298220    c  W95 FAT32 (LBA)
/dev/sda3            3020        4864    14819962+   5  Extended
/dev/sda5            3020        4781    14153233+  83  Linux
/dev/sda6            4782        4864      666666   82  Linux swap / Solaris

Contents of /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=b4a555b2-d451-4886-b3f1-d582a7e86801 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=99000618-0a53-40fa-a33a-7d1f3f03a5be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Contents of /etc/mtab:
/dev/sda5 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/sdb1 /media/disk vfat rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000 0 0

Thanks for your help.

Cheers.

---

### Post by Zorael on 2008-05-01
I'm not an expert on fstab options, but this is copied from my fstab (and adapted to your disk), and should work. Make a backup of that /etc/fstab and then replace the contents of the real one with this.
```
# /etc/fstab: static file system information.
#
# <file system>	<mount point>	<type>	<options>	<dump> <pass>
proc		/proc		proc	defaults	0	0
# /dev/sda5
UUID=b4a555b2-d451-4886-b3f1-d582a7e86801 / ext3 realtime,errors=remount-ro 0 1
# /dev/sda2, don't know your UUID
/dev/sda2	/media/windows	vfat utf8,umask=007,gid=46 0 **2**
# /dev/sda6
UUID=99000618-0a53-40fa-a33a-7d1f3f03a5be none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```
Change the 2 in bold (the last digit at the end of the line beginning with /dev/sda2) to **0** to make it skip checking the filesystem of that drive upon boot. FAT systems take stupid long to check, so it'll prolong boot time. Of course, this means the filesystem isn't checked regularly (which is dangerous, especially if you every now and then get dirty shutdowns of your system. See below on how to force a check.

Anyway, to proceed, enter this.
```
$ sudo mkdir /media/windows
$ sudo mount -a
```
The device *should* now be mounted in /media/windows. I'm not sure if it's a dirty fix, but you should be able to get write permissions by changing the ownership of the mount directory.
```
$ sudo chown youruser /media/windows
$ sudo chgrp yourgroup /media/windows
```
Of course, replace yourname and youruser with your login name and group. If you don't know your group name, it's likely the name of your user. Enter this to see a list of the available ones; it's usually the first in the list.
```
$ groups
```
Replace **all** occurences of **/media/windows** mentioned here to mount it elsewhere. Someone else more knowledgeable could give you advice as to which options to put in the /etc/fstab line to optimize stuff.


[INDENT]To force a check, enter this.
```
$ sudo umount /media/windows
$ sudo fsck /dev/sda2
$ sudo mount -a
```[/INDENT]

---

### Post by richardy on 2008-05-04
Hi Zorael,
It works, so thanks a lot for that. There was only one minor issue and that was with the commands:

$ sudo chown richard /media/windows
$ sudo chgrp richard /media/windows

Which weren't allowed (a bit odd).

But at the mom net i am not to bothered since i can now access windows.
Anyway - thanks again.

Cheers.

---

### Post by Zorael on 2008-05-04
Looking at my mount, I don't think you'd actually have to;
```
zorael@sunspire:~$ ls -l /media
total 44
drwxr-xr-x  2 root root     4096 2008-04-28 05:13 cdrom
drwxrwxr-x 14 root zorael   4096 2008-05-03 18:23 main
drwxrwxr-x  8 root zorael   4096 2008-04-29 16:38 misc
drwxrwx--- 18 **root plugdev** 32768 1970-01-01 01:00 windows
```
Perhaps a reboot is needed, though I have my doubts.

---

