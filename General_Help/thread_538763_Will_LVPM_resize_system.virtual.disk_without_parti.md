---
title: "Will LVPM resize system.virtual.disk without partitioning?"
date: 2007-08-30
forum: General Help
---

### Post by SyCo123 on 2007-08-30
Looks like the wubi wiki changed in the last few days.
[https://wiki.ubuntu.com/WubiGuide#head-5aac3daad4eb9fcc3502ba1a4d6891b71b050b1d](https://wiki.ubuntu.com/WubiGuide#head-5aac3daad4eb9fcc3502ba1a4d6891b71b050b1d)

There was a set of commands to resize system.virtual.disk now it just says use LVPM. I've read up on it but it looks like it just transfers wubi to a partitioned ubuntu install. 

Doesn't that defeat the point of wubi? Great if you want to change to a partitioned install but I simply want to increase my 4gb install to 8 gb as I've run out of space. I still don't want to partition my hard drive which is why im using wubi.

Does anyione know where the old instructions are or am i mis understanding LVPM and it can resize system.virtual.disk as well?

---

### Post by hh93 on 2007-08-30
> **SyCo123 said:**
> Looks like the wubi wiki changed in the last few days.
[https://wiki.ubuntu.com/WubiGuide#head-5aac3daad4eb9fcc3502ba1a4d6891b71b050b1d](https://wiki.ubuntu.com/WubiGuide#head-5aac3daad4eb9fcc3502ba1a4d6891b71b050b1d)

There was a set of commands to resize system.virtual.disk now it just says use LVPM. I've read up on it but it looks like it just transfers wubi to a partitioned ubuntu install. 

Doesn't that defeat the point of wubi? Great if you want to change to a partitioned install but I simply want to increase my 4gb install to 8 gb as I've run out of space. I still don't want to partition my hard drive which is why im using wubi.

Does anyione know where the old instructions are or am i mis understanding LVPM and it can resize system.virtual.disk as well?

Yup... but make sure your file system is NTFS not FAT32.
see [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)
for ilustration see : [http://ubuntuforums.org/showthread.php?t=505628&page=2](http://ubuntuforums.org/showthread.php?t=505628&page=2) and [http://ubuntuforums.org/showthread.php?t=529084&page=3](http://ubuntuforums.org/showthread.php?t=529084&page=3)

---

### Post by SyCo123 on 2007-08-30
Thanks for the links hh93. I did search the forums before posting, but clearly not well enough!!

---

### Post by hh93 on 2007-08-30
> **SyCo123 said:**
> Thanks for the links hh93. I did search the forums before posting, but clearly not well enough!!

did you get it to work?

---

