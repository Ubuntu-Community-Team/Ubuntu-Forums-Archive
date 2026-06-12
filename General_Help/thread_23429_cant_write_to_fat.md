---
title: "cant write to fat"
date: 2005-04-01
forum: General Help
---

### Post by h4n9m4n on 2005-04-01
well, i just reinstalled ubuntu because it was getting a little cluttered. It was 4.10 upgraded to hoary. But now when i install hoary with the hoary cd, it seems i cant write to my fat partition. I have it mounted as /storage. its on the same disk as ubuntu, Im fairly new to the inner workings of linux so if anybody has some easy way to fix this itll be appreciated. Before i could write to it, but now i cant. help?

---

### Post by Buffalo Soldier on 2005-04-01
What's the content of your */etc/fstab* file and the output from typing the **sudo fdisk -l** command in console?

---

### Post by h4n9m4n on 2005-04-02
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               reiserfs notail          0       1
/dev/hdb2       /storage        vfat    defaults        0       0
/dev/hdb3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows    ntfs    umask=0222      0       0
```

thats my fstab.
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
16 heads, 63 sectors/track, 119150 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       73345    36965533+  83  Linux
/dev/hdb2           73345      117061    22033147+   b  W95 FAT32
/dev/hdb3          117061      119149     1052257+  82  Linux swap / Solaris
```

thats fdisk -l.

---

### Post by Akrame on 2005-04-02
i think that you should replace your /Dev/hdb2 line in fstab by this: 



/dev/hdb2     /storage     vfat     defaults,auto,uid=1000,gid=1000   0   0

---

### Post by h4n9m4n on 2005-04-07
thanks alot, but how do i make it so normal users can modify contents too? because right now only root has the power to access and modify contents

---

### Post by Klin'Targ on 2005-04-08
[QUOTE=h4n9m4n]thanks alot, but how do i make it so normal users can modify contents too? because right now only root has the power to access and modify contents[/QUOTE]
 add ",umask=000" to the end of that string of comma deliminated options giving:

/dev/hdb2 /storage vfat defaults,auto,uid=1000,gid=1000,umask=000 0 0

Edit: Note that I don't usually use uid=1000,gid=1000. You may have to remove these to get umask to work; I'm not sure.

---

