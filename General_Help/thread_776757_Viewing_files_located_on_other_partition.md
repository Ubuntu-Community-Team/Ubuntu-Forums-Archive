---
title: "Viewing files located on other partition"
date: 2008-04-30
forum: General Help
---

### Post by jworld789 on 2008-04-30
Ok this may sound like a complete noob question and there;s probably already people who've asked this question already but I recently installed Ubuntu on a second partition as a dual boot with windows xp and I want to be able to access all of the files currently located on windows from ubuntu. Is there an easy way to do this or does it have to be complicated?

---

### Post by bodhi.zazen on 2008-04-30
"Easy" is relative.

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: 
[list=number]
[*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent]
[/list]

---

