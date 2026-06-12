---
title: "[SOLVED] fstab"
date: 2007-12-01
forum: General Help
---

### Post by jopusbob on 2007-12-01
hey guys im trying to have 2 sata hard drive auto mount to seperate but certain places and can't figure out exactly how.  here is the current fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8c4edb36-25ea-4689-88ee-e0128e725e32 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c22418e5-5718-4e66-9c37-914a34ae0748 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#Added by diskmounter utility
/dev/sdb1 /media/sdb1 ntfs ro,user,fmask=0111,dmask=0000 0 0

the two drives i want to add are sdc1 and sdd1, also i want them to auto mount on startup.
if anyone could help it would be much appreciated.

---

### Post by PmDematagoda on 2007-12-01
1)Open up Nautilus in root mode:-
```

sudo nautilus
```

2) Then navigate to the /media directory and create two new directories, you may name them whatever way you want but I recommend that there be no spaces.

3) Open the fstab file for editing using:-

```
sudo gedit /etc/fstab
```

Then add the required lines:-

```
/dev/sdc1 /media/nameof1folder and fill the other options according to the file system you use.
```

Do the same to the other one except that you use the second folder.

---

### Post by bodhi.zazen on 2007-12-01
See this link [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by jopusbob on 2007-12-01
thank you very much my problem is now solved

---

