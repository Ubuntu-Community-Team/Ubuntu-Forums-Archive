---
title: "Mount NTFS partitions on boot-up"
date: 2008-03-11
forum: General Help
---

### Post by 6205 on 2008-03-11
Hello,

Please can some profi write me here correct "Mount options" parameters to get NTFS partitions automaticaly mounted for write support when my Gutsy boots up ? And also without that annoying root pasword prompt. My hard-drives are in preview image, thank you for help...

---

### Post by Rocket2DMn on 2008-03-11
Sure, can you post the outputs of
```
sudo fdisk -l
cat /etc/fstab
```
If you know which device it is, please say which.

---

### Post by 6205 on 2008-03-11
[COLOR="Blue"]laco@home-desktop:~$ sudo fdisk -l[/COLOR]

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49244923

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1958    15727603+   7  HPFS/NTFS
/dev/sda2            1959        8485    52428127+   7  HPFS/NTFS
/dev/sda3            8486        9674     9550642+  83  Linux
/dev/sda4            9675        9733      473917+   5  Extended
/dev/sda5            9675        9733      473886   82  Linux swap / Solaris

[COLOR="Blue"]laco@home-desktop:~$ cat /etc/fstab[/COLOR]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d7cd168f-0f25-49cc-a568-db9ddfac6b0c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=66d0aac8-2541-4778-9af7-a919f7712e64 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by Rocket2DMn on 2008-03-11
OK, we'll add the correct lines to your fstab file.
```
gksudo gedit /etc/fstab
``` and add
```
/dev/sda1 /media/[mount_point1] ntfs-3g defaults,locale=*en_US.utf8* 0 0
/dev/sda2 /media/[mount_point2] ntfs-3g defaults,locale=*en_US.utf8* 0 0
```
I see you are using a different language system, so where I have italicized locale=blahlbah, you should replace (if needed or wanted) with the correct phrase from
```
locale -a
```
Save and close.

The /media/[mountpoint] portions are where you want to mount the partitions - you will have to create them before you attempt to mount, so for example:
```
sudo mkdir /media/partition1
sudo mkdir /media/partition2
```

When all that is setup, run
```
sudo mount -a
```

If there are errors, post them here and we will fix the problems.

---

### Post by froy02 on 2008-03-11
The easiest way of mounting NTFS partitions is use synaptics package installer to install ntfs-config.  After installation go to Applications -> System tools -> NTFS config.  Click on the program and it would show your NTFS partitions that are available for mounting.  Put a check mark on all the partitions you want to be mounted at start up.  It will do the rest and you are done.

---

### Post by 6205 on 2008-03-12
Thanks both for help. Looks like ntfs-config did it.

---

