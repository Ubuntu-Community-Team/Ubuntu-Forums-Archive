---
title: "NTFS 3g was working fine now i cant see anyfiles"
date: 2007-02-22
forum: General Help
---

### Post by Andy1571 on 2007-02-22
i set up linux so it could read and write to my windows ntfs partition using ntfs 3g(this used to work fine).  Today i turned on my PC and when i open up that partition no files show up from my windows drive even though it appears that the harddrive is mounted.. any assistants would be much appreicated.

/dev/hda1   *           1        8900    71489218+   7  HPFS/NTFS
/dev/hda2            8901        9729     6658942+   f  W95 Ext'd (LBA)
/dev/hda5            8901        9665     6144831   83  Linux
/dev/hda6            9666        9729      514048+  82  Linux swap / Solaris
hda1 is my windows drive

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1 /media/windows ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

if you need anymore information just ask

Manythanks Andy..

---

### Post by givré on 2007-02-22
Your partition is probably not mounted.
To know the mounted partition run in terminal :
```
cat /etc/mtab
```
To mount all your partition :
```
sudo mount -a
```
If ntfs-3g can't mount your partition, it will say you why.

---

### Post by Andy1571 on 2007-02-25
Found the problem, it had just started to mount to a different destination.  All fixed now, thx for ur help.

---

