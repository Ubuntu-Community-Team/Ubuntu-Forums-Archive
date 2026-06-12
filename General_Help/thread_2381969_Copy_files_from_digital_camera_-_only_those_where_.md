---
title: "Copy files from digital camera - only those where archive attribute is set"
date: 2018-01-07
forum: General Help
---

### Post by sprinterdriver on 2018-01-07
Hi.

I know that the attributes of FAT/FAT32 is a windows thing, but anyway - is it possible to somehow copy only the files (on SD card) that have FAT attribute set?

So far I have not found a way to separate or sort files on a fat32 drive based on the attributes (archive, hidden, system, .. . )

Thanks for suggestions.

---

### Post by TheFu on 2018-01-07
Possible? Somehow?

Sure.

Write a script that filters the file list as you like, then only copy those files over. Let me spend 5 minutes seeing if I can do it.  Pulled an SDHC card from a Canon PnS ... 

So the mount options are:
$ mount |grep CAN
/dev/sdb1 on /media/jp/CANON_DC type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)

That lead me to a tool I've never heard about previously, 
```
$ fatattr *
     a   650.JPG
     a   651.JPG
 h   a   652.JPG
     a   653.JPG
  s  a   654.JPG
     a   655.JPG
     a   656.JPG

```
So you can filter using any tool you like (grep/awk/perl/python) on the columns in the output from that tool.

However, I find it easier to just copy all the files and delete the camera memory.  Then, when they are on a real computer, I can do anything. Of course, the 'copy' to Linux file system will drop the MS-DOS attributes.  SDHC storage isn't exactly safe. We all need backups.

---

### Post by Holger_Gehrke on 2018-01-07
The program fatattr from the package of the same name can show and change FAT file attributes. To copy only files with the archive attribute set, you'd do something like
```

cp $(fatatr /media/me/fatsdcard/*|grep [^.....a]|cut -c 10-) /home/me/Pictures

```

Holger

---

### Post by sprinterdriver on 2018-01-09
Thanks very lot you guys - I was almost to give up :popcorn:

I have to try this for myself tomorrow.

And then - I guess fatattr can also remove the attributes from files.

Just for the sake of havin it said - I also asked the same question on a norwegian user forum. Theree was this guy suggested me using a program named "rapid Photo Downloader", so I did. That program is solely ment for transfering images and video files from a memory card to a local folder. But the name make me normally  assuming it's som shady program that I don't want to have - having used windows since the 90's I have also seen a lot of names on shady software (have make my share of blunders and then getting flooded with crapware), and this name wouldn't stick out from the rest of the pool).
But I actually tested the program and it worked. If dealing with files that isn't solely images and videos, the program isn't up to the task of course.

---

### Post by dlynch3 on 2018-01-17
> **sprinterdriver said:**
> 
But I actually tested the program and it worked. If dealing with files that isn't solely images and videos, the program isn't up to the task of course.
If you do end up using it please consider contributing to the [Norwegian translations]("https://translations.launchpad.net/rapid/pyqt/+pots/rapid-photo-downloader"). Thanks.

---

