---
title: "Mounting an NTFS partition"
date: 2007-05-06
forum: General Help
---

### Post by ian.gralinski on 2007-05-06
I've got an NTFS partition on the hard drive where Ubuntu is installed. I was wondering whether it's possible to create a shortcut on the desktop to it that will make it read accessible to all users? 

The only success I've had is by manually mounting the drive (to /media/hdd2) in gparted, and then opening it as root. When I try to edit the properties of the folder, I get the error message: "Couldn't change the owner of "hdd2" because it is on a read-only disk". 

I've also tried adding this line to fstab:
/dev/hdb2       /media/hdd2     ntfs-fuse auto,gid=1001,umask=0002 0 0
where all users have been added to group 1001. 

I have a full NTFS hard drive that has no problems auto-mounting on startup...

---

### Post by lw5 on 2007-05-06
Are you using ntfs-3g? Did you have a look at [_this_](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)?

---

