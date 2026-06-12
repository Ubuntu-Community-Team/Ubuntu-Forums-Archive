---
title: "NTFS Mount Problems"
date: 2006-12-13
forum: General Help
---

### Post by penguinchrissy on 2006-12-13
I have gone through the install of ntfs-3g to try and write to my windows partation. Since I went through it there are no files in the mounted folder it just tells me how much free space there is. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c6309981-7cd3-4b6e-960e-7dca72390cbf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2 /media/windows  ntfs-fuse    auto,gid=1001,umask=0002    0    0
# /dev/sda3
UUID=92f72103-e9cf-4cc5-b56a-14045756db54 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

thats what my fstab looks like.
I also tried it this way the first one was just my last attempt to get it working neither works.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c6309981-7cd3-4b6e-960e-7dca72390cbf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2 /media/windows  ntfs-3g    defaults,locale=en_US.utf8    0    0
# /dev/sda3
UUID=92f72103-e9cf-4cc5-b56a-14045756db54 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by strabes on 2006-12-13
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

Did you sudo mkdir /media/windows  ?

---

### Post by penguinchrissy on 2006-12-15
I think I found out what the problem was
# /dev/sda2 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
I think the # sign was causing the problem I took it out and it works now.

---

### Post by penguinchrissy on 2006-12-15
Now all I need to know is how to recreat the icons for my desktop and in computer.

---

