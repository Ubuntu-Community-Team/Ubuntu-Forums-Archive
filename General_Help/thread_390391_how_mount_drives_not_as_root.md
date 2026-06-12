---
title: "how mount drives not as root?"
date: 2007-03-21
forum: General Help
---

### Post by pizpot on 2007-03-21
Hi, I am running Ubuntu6.10. I am trying to use a 2nd hardrive as a place to keep all my data. The 1st hardrive is triple boot. Everything is fine, except the 2nd hardrive (and the non-ubuntu partitions on 1st drive) get mounted and everything is owned by root.

Like a fool I actually cd'ed to the 2nd drive and did a "chown -R pizpot:pizpot * but it said error, error, error... instead of doing something to the files. Whew no harm done.

What I am after is a way to have them mounted to the current user, not root. I wonder if it is something you can put in fstab? Come to think of it, having chown work is probably the desired solution, I don't know.

--
Pizpot

---

### Post by taurus on 2007-03-21
What filesystem is it anyway and how do you mount it, from /etc/fstab?

---

### Post by Kateikyoushi on 2007-03-21
You can find more info about it in the wiki. [LINK]("http://ubuntuguide.org/wiki/Dapper")

To be able to help we need to see your fstab 
> cat /etc/fstab
and the output of the following command
> sudo fdisk -l

---

### Post by pizpot on 2007-03-21
It is a 120G fat32 partition. I guess I made it with gparted. Yes it is mounted with fstab. Here are those outputs:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=5be1bc13-78a1-45fe-b132-10a49d4d0862 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=F3C9-1244  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=1B0F-1576  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=45E2-071F  /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=4b507cff-9945-4662-b262-8a8b2ccf623a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


####################################################

Disk /dev/hda: 30.0 GB, 30020272128 bytes
16 heads, 63 sectors/track, 58168 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3949     1990075+   6  FAT16
Partition 1 does not end on cylinder boundary.
/dev/hda2            3949       27728    11984490    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda3           27732       56085    14289817+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda4           56085       58156     1044225   82  Linux swap / Solaris
Partition 4 does not end on cylinder boundary.

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       13063   104928516    b  W95 FAT32

---

### Post by pizpot on 2007-03-24
I've been thinking about this problem. I think root is fine to own the fstab mounted drives. As not-root I am able to do everything with those areas. I can make folders, delete files. The only thing I can't do, that I know about, is change permissions. When I right click on a file in Nautilus, properties says You Are Not the Owner.

I just tried the command prompt, same thing.

---

### Post by bodhi.zazen on 2007-03-24
These partitions are all vfat, so use uid=1000

Like this :

UUID=F3C9-1244 /media/hda1 vfat defaults,utf8,umask=007,**uid=1000,gid=100** 0 **2**
# /dev/hda2
UUID=1B0F-1576 /media/hda2 vfat defaults,utf8,umask=007,**uid=1000,gid=100** 0 **2**
# /dev/hdb1
UUID=45E2-071F /media/hdb1 vfat defaults,utf8,umask=007,**uid=1000,gid=100** 0 **2**

Note IN THE LAST COLUMN CHANGE THE 1 TO 2 ( 1 should be used for the root partition , 2 for the rest)

This should set the owner to your user name and group to users :)

---

### Post by pizpot on 2007-03-24
Good tip!!

---

