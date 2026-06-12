---
title: "udf dvd-r fails to mount"
date: 2007-10-24
forum: General Help
---

### Post by tbuss on 2007-10-24
Sony PSP DVD-R contains PSP game data. Data was burned to disc using windows Vista. Disc fails to mount when inserted into optical drive using Ubuntu Gutsy 7.10

The follwoing error message displays:

> Cannot mount volume

Invalid mount option when attempting to mount the volume 'UDF Volume'.

**Tried:**
```
-sudo gedit /etc/fstab
```
**Changed** ```
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto 0 0
```
**and**
```
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
```
**to**
```
/dev/scd1 /media/cdrom0 auto user,noauto 0 0
/dev/scd1 /media/cdrom1 auto user,noauto 0 0
```
**Also Tried switching the order of the entries in fstab**
```
/dev/hda        /media/cdrom0       iso9660,udf user,noauto     0       0
/dev/hda        /media/cdrom1       iso9660,udf user,noauto     0       0
```
**Tried manual:**
```
~$ sudo mount /dev/scd0 -t udf /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Anyone have any suggestions?

---

