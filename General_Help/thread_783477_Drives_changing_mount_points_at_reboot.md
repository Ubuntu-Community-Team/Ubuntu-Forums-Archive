---
title: "Drives changing mount points at reboot"
date: 2008-05-05
forum: General Help
---

### Post by ztirffritz on 2008-05-05
I've installed 8.04 x64.  I have 2 internal drives and 1 external firewire drive.  One of the internal drives is the boot drive.  The other was just going to be storage space.  I edited fstab to mount the extra internal drive and the external FW drive as they were then identified.  I've found that almost everytime that I reboot the drives seem to change their designation.  On one reboot the external drive is /dev/sdc on the next boot it is /dev/sda.  This makes my fstab wrong and it screws up links and some of the system configurations.  Why is everything moving around at boot?  My fstab is below:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=433287db-55c9-4512-9634-91816d90f455 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=6faf656f-3b0b-4ebc-9a35-cad8775a8c43 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1       /media/disk-1                           ext3            defaults 0 0
/dev/sdc1       /media/disk-2                           ext3            defaults 0 0

---

### Post by WillieDaPimp on 2008-05-05
I am having the same problem.




***willie@harvey:~$ ls /media/
***cdrom   hdb1    OpenGEU 7.10LN  Storage_   Storage___
***cdrom0  laptop  Storage         Storage__  Storage____
***willie@harvey:~$ 


The OpenGEU was a cd I looked at about three weeks ago. Storage is my external hard drive that changes at every reboot. Thats crazy. Never done this in an ubuntu release before.

---

