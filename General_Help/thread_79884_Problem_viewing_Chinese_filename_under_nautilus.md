---
title: "Problem viewing Chinese filename under nautilus"
date: 2005-10-21
forum: General Help
---

### Post by c24chan on 2005-10-21
Hi,

I am new to Ubuntu and I was wondering if anyone can help me with the following problem.

I am currently dual booting ubuntu with WinXP and I have some file with chinese filename in a FAT partition, the following is my fstab.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs notail          0       1
/dev/hda1       /media/hda1     ntfs    ro        0       0
/dev/hda2       /media/hda2     vfat    users,exec,rw,codepage=950,iocharset=big5        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

as you can see I use codepage=950 and iocharset=big5.

However, it displayed as invalid encoding under nautilus.

Can anyone help me with this?

Thanks in advance.

---

### Post by mykey on 2005-10-21
try **sudo dpkg-reconfigure locales** and add the locale for the language you want displayed e.g. zh_HK BIG5-HKSCS

---

### Post by c24chan on 2005-10-22
Hm...

Tried it, doesn't seem to do the trick...

Any more ideas?

---

### Post by xingmu on 2005-10-22
Are you sure the files are using BIG5 encoding?  I know that Chinese XP can do that, but it seems that the majority of your files should be in Unicode (and only some legacy BIG5 programs will create BIG5 files, right?).  I may be wrong about this.  Anyways, when I was dual-booting with XP using utf8 for my charset was all I needed.

Hope that helps.

---

