---
title: "Dual Boot Load Time"
date: 2007-11-30
forum: General Help
---

### Post by Hanyou on 2007-11-30
Hello I'm very new to Linux and I have a dual boot of 7.10 with xp on the second partion. My problem is when Linux loads up it takes upwards of 5 minutes for it to load up because it checks xp's partion for errors. Is there any way I can disable this or speed it up for a faster boot time? Any help would be greatly appreciated!

---

### Post by navaburo on 2007-12-01
Below is my /etc/fstab file. It controls the mounting of drives. I am not sure exactly where it tells the machine to check for errors, but I know that my machine doesn't check for errors on the XP partitions (the lines involving ntfs).

Maybe you could check for differences between mine and yours.

```

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda6

UUID=ac41211d-b338-43e9-be83-f982a59c67d8 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda1

UUID=4962D116FBE242C4 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1

# /dev/sda2

UUID=1258B444ACD747D1 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1

# /dev/sda5

UUID=64c7a3ac-2a8e-46f0-ac82-0ba756396175 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

~                                                                                                                

~                                                                                              

```

best of luck

---

