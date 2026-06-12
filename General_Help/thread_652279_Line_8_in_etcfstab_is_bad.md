---
title: "Line 8 in /etc/fstab is bad"
date: 2007-12-28
forum: General Help
---

### Post by WaySensei on 2007-12-28
When running powertop and trying to enable noatime, I get the warning: line 8 in fstab is bad
My /etc/fstab is reproduced below:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=df5f33bf-8cc8-49c3-946d-24ef8a65dd9d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3F3C-1AF6  /media/EFI      System  Partition       vfat    defaults,utf8,umask=007,gid=46 0 1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

VIM indicates that the line beginning with vfat and ending with gid=46 0 1 is the trouble-maker. Can someone please show me how to correct this? In addition, I would like to know what problems this bad line may be causing in my system. I'm fairly new to Linux so please bear with me. :)

---

### Post by bonzodog on 2007-12-28
Yes, the words 'system partition' should not be in the file.
not sure why they are there?

---

### Post by geirha on 2007-12-28
```
UUID=3F3C-1AF6  /media/EFI      [color=red]System  Partition[/color]       vfat    defaults,utf8,umask=007,gid=46 0 [color=orange]1[/color]
```
Red marks the offending part. If the mount point should be /media/EFI, then remove the two words System and Partition. If the mount point should be "/media/EFI System Partition", then change the line to read: 
```
UUID=3F3C-1AF6  /media/EFI\040System\040Partition       vfat    defaults,utf8,umask=007,gid=46 0 2
```

Also, the last digit should be 2, not 1. All this is explained in the man-page of fstab, so read it by running ```
man fstab
```

---

### Post by WaySensei on 2007-12-28
Problem solved! I had to add one additional detail to that line to prevent it from mounting my EFI partition upon boot:
```
UUID=3F3C-1AF6  /media/EFI	vfat    defaults,noauto,utf8,umask=007,gid=46 0 2

```
But now all is well. Once again, the Ubuntu community proves its quality!

---

