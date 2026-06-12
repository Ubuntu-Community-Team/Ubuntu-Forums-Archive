---
title: "Help unmounting the sda1"
date: 2008-03-31
forum: General Help
---

### Post by harryliddic on 2008-03-31
I have through some advice and my own ignorance mounted the sda1 in a file /media/windrive under the root directory. Now I can't seem to access it for wine and aramok, can I unmount the sda1 from the root directory and mount it /media/sda1?

---

### Post by Slushdoot on 2008-03-31
```
sudo umount /dev/sda1
``` That should unmount it, no matter where it's mounted.

If you have it entered in fstab, you can remount it in the usual place with ```
sudo mount -a
```

---

### Post by harryliddic on 2008-03-31
I tried sudo mount  -a here were the results


NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
harry@harry-desktop:~$ 

any ideas on what to do next?

---

### Post by Slushdoot on 2008-03-31
What does ```
sudo fdisk -l
``` return?

---

### Post by harryliddic on 2008-03-31
it returns

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60466447

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865        9484    37110150   83  Linux
/dev/sda3            9485        9729     1967962+  82  Linux swap / Solaris

Disk /dev/sdb: 1031 MB, 1031306752 bytes
32 heads, 63 sectors/track, 999 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0xedba4c3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         969      976562+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2             970         999       30240   82  Linux swap / Solaris
harry@harry-desktop:~$

---

### Post by jocko on 2008-03-31
and what do you get from this:
```
cat /etc/fstab
```?

---

### Post by harryliddic on 2008-03-31
the following

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=05cd73b0-8103-4e6a-8685-8b494ede9871 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=6AE45588E4555801 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=a5bf7916-dee5-4eb0-b81a-81bec1ee1906 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
harry@harry-desktop:~$

---

### Post by jocko on 2008-03-31
hmm... all looks ok to me... what about:
```
ls -l /dev/disk/by-uuid/
```?

---

### Post by harryliddic on 2008-03-31
this here



ls: invalid option -- /
Try `ls --help' for more information.

---

### Post by harryliddic on 2008-03-31
my mistake here the result

harry@harry-desktop:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-03-29 22:15 05cd73b0-8103-4e6a-8685-8b494ede9871 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-03-29 22:15 6AE45588E4555801 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-03-29 22:15 a5bf7916-dee5-4eb0-b81a-81bec1ee1906 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-03-30 05:15 ca6bce26-6b6d-4ed1-9cfd-6215ea2fafda -> ../../sdb2
harry@harry-desktop:~$

---

