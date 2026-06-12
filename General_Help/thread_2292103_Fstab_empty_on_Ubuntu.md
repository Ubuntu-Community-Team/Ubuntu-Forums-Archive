---
title: "Fstab empty on Ubuntu"
date: 2015-08-25
forum: General Help
---

### Post by claudio-paravano on 2015-08-25
Hi all,
I have the following problem.I Installed successfully UBUNTU 15.04 on SD card for Wandboard embedded board.I have removed some packages to reduces root size.
The original fstab file was: 

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
UUID=763ebee8-1888-4f12-b21a-54f9054dd326 /               ext4    errors=remount-ro 0       1
UUID=addbbc5a-574e-4846-a679-f568a530bc3c /boot           ext2    defaults        0       2
UUID=f4472925-5152-4e21-96a0-cee254ea28dd none            swap    sw              0       0

after the fstab modified was :
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
UUID=763ebee8-1888-4f12-b21a-54f9054dd326 /               ext4   defaults,noatime,nodiratime,commit=1600,errors=remount-ro 0       1
tmpfs    /home/alfa/ramdisk tmpfs    nodev,nosuid,noexec,nodiratime,size=128M    0    0
UUID=addbbc5a-574e-4846-a679-f568a530bc3c /boot           ext2    defaults        0       2

After fstab modification , rebooted pc
I discovered that the fstab file was empty,and  typing the "mount" command was not present the new directives included in fstab.


 
 
 After I copied the content again fstab file modified.
 Consequence: the S.O. Linux does not seem to take into account the directives of the configuration file fstab
 Why can 'happen this?

Thanks a lot

Claudio

---

