---
title: "how does nautilus decide what drives/partitions to display?"
date: 2007-12-24
forum: General Help
---

### Post by radradrobotanks on 2007-12-24
Hello,

I have used dmraid to install ubuntu over a raid0 array. The raid0 array uses two sata disks. Nautilus for some unknown reason displays a removable media icon named xp (like for cdrom or floppy) for what i think is a non sense partition. How would I stop this non sense partition showing up as a icon and in the side bar in nautilus?

   - the non sense partition is not listed in fstab

Here is the exact error when returned after double clicking on the icon and entering my password at the prompt:

"Cannot mount volume.

Unable to mount the volume 'XP'.

Details

fuse: mount failed: Device or resource busy FUSE
mount point creating failed Unmounting /dev/sda1 (XP)"

Since /dev/sda1 forms part of my raid0 array it would make sense that /dev/sda1 would not be able to be mounted. (missing stripes stored on /dev/sdb1). I dont want to mount /dev/sda1 I want to stop a icon for it showing up in nautilius.

Thanks

---

### Post by zarqoon on 2007-12-25
It seems that some people had this kind of problem before
The solution is in post 34 in this thread
[http://ubuntuforums.org/showthread.php?t=428196&page=4]("http://ubuntuforums.org/showthread.php?t=428196&page=4")

---

### Post by radradrobotanks on 2008-01-02
Thanks worked well 7.10 gutsy

---

