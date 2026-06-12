---
title: "Write access to Windows partition"
date: 2005-10-22
forum: General Help
---

### Post by JamesNorris on 2005-10-22
Back using Horay, I set my fstab file to allow read only access to my NTFS partition and write access to my FAT32 partition. I've not changed fstab at all while upgrading to breezy, but for some reason, I can't write to my FAT32 partition. I've attached my fstab below, any help would be great!
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb7       /home           ext3    defaults        0       2
/dev/hda1       /mnt/win_c     vfat    defaults        0       0
/dev/hdb2	/mnt/win_d	ntfs	ro,nls=utf8,umask=0000	0	
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by paddyg on 2005-10-22
[QUOTE=JamesNorris]Back using Horay, I set my fstab file to allow read only access to my NTFS partition and write access to my FAT32 partition. I've not changed fstab at all while upgrading to breezy, but for some reason, I can't write to my FAT32 partition. I've attached my fstab below, any help would be great!
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
.........................
/dev/hda1       /mnt/win_c     vfat    defaults        0       0
/dev/hdb2	/mnt/win_d	ntfs	ro,nls=utf8,umask=0000	0	
.............................

```[/QUOTE]

I don't understand... you set ntfs to ro and umask 0000 (= everybody can read, write and execute files)? Why don't you try vfat umask 0000?

---

### Post by JamesNorris on 2005-10-22
[QUOTE=paddyg]I don't understand... you set ntfs to ro and umask 0000 (= everybody can read, write and execute files)? Why don't you try vfat umask 0000?[/QUOTE]

oops, that umask was suppose to be for the vfat partition... lmao, I wonder how that got there... surprised it's never complained about that... 

I'll try putting that back where it belongs...

edit: yep, that's the one. Thank for pointing that out for me :) :KS

---

