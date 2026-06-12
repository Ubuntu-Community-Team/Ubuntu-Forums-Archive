---
title: "HELP - Windows ntfs partion write/delete files permissions"
date: 2006-12-20
forum: General Help
---

### Post by MJSOnline on 2006-12-20
Hi all.  I cannot write/delete files from my Windows XP ntfs drive/partion.

Below is a copy of my FSTAB file.  Can anyone point me in the right direction or tell me where I am going wrong?  Thanks. Matthew

```
  GNU nano 1.3.12             File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=f49f4026-3626-4e7b-8a7d-e447daf397b7 /               ext3    defaults,erro$
# /dev/hda1
UUID=34B43B8BB43B4F1C /media/hda1     ntfs    nls=utf8,fmask=0333,dmask=0222   $
# /dev/hdb1
UUID=F4DF-7B50  /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=6e9afc4d-c0a5-4075-91b9-1c11600945dd none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by ciscosurfer on 2006-12-20
> **MJSOnline said:**
> Hi all.  I cannot write/delete files from my Windows XP ntfs drive/partion.

Below is a copy of my FSTAB file.  Can anyone point me in the right direction or tell me where I am going wrong?  Thanks. Matthew

```
  GNU nano 1.3.12             File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=f49f4026-3626-4e7b-8a7d-e447daf397b7 /               ext3    defaults,erro$
# /dev/hda1
UUID=34B43B8BB43B4F1C /media/hda1     ntfs    nls=utf8,fmask=0333,dmask=0222   $
# /dev/hdb1
UUID=F4DF-7B50  /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=6e9afc4d-c0a5-4075-91b9-1c11600945dd none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```By default, you cannot write to NTFS partitions in Ubuntu.  [The NTFS-3G thread]("http://ubuntuforums.org/showthread.php?t=217009") may be of assistance. :D

---

### Post by MJSOnline on 2006-12-20
> **ciscosurfer said:**
> By default, you cannot write to NTFS partitions in Ubuntu.  [The NTFS-3G thread]("http://ubuntuforums.org/showthread.php?t=217009") may be of assistance. :D

Thanks for the link..  If I converted my ntfs partion, only 5GB in size, to FAT32 would that work then?  How would it work?  Thanks.

---

### Post by ciscosurfer on 2006-12-20
> **MJSOnline said:**
> Thanks for the link..  If I converted my ntfs partion, only 5GB in size, to FAT32 would that work then?  How would it work?  Thanks.Yes, FAT32 in Ubuntu is by default a read/write filesytstem (in the eyes of Ubuntu).  If you want to convert it, I believe you'll have to reformat that partition to FAT32 (in other words, back up your data on your current NTFS parititon, then reformat it as FAT32, then you can place all backed-up data back on the parititon and Ubuntu should be able to allow you to read and write from it).

---

### Post by MJSOnline on 2006-12-20
Ok I reinstalled my Windows XP system and then ubuntu. I have the grub menu working fine but still can not write to my winxp partion, now in FAT32 and also my Data partion still in FAT32.  Can anyone give me the answer as I am pulling my hair out now!! Thanks. Matthew

---

### Post by MJSOnline on 2006-12-21
BUMP!! Anyone got the answer?  I can mount them, read but cannot write to them. Thanks again. M

---

### Post by Zalbor on 2006-12-21
Windows XP can only be installed in NTFS. Ergo, you can't write to that partition with the default driver.

---

### Post by MJSOnline on 2006-12-21
> **Zalbor said:**
> Windows XP can only be installed in NTFS. Ergo, you can't write to that partition with the default driver.

That is not true.  I have it installed as  FAT32.  I just cannot write to it. M

---

### Post by ciscosurfer on 2006-12-21
> **MJSOnline said:**
> That is not true.  I have it installed as  FAT32.  I just cannot write to it. MTry setting the following in your /etc/fstab, in order to make your FAT32 partitions read/write accessible:```
# /dev/hdb1
UUID=F4DF-7B50  /media/hdb1    vfat   umask=0000    0   0
```

---

