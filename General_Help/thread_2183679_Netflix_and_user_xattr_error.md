---
title: "Netflix and user_xattr error"
date: 2013-10-25
forum: General Help
---

### Post by lsutiger on 2013-10-25
I am trying to use the Netflix app on my mythbuntu install. I follwed the instructions from the wiki but I am receiving the user_xattr error when trying to run. I have remounted and rebooted for good mesure with the same result.
I do understand this subject has been posted here before, but do not have a solution other than adding the user_xattr field to thew fstab (as far as I can see).

 The following is the fstab file:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ff0f0f33-737e-40b6-aaf0-4e42252a4cb3 /               ext4    errors=remount-ro,user_xattr       0       1
# /home was on /dev/sda2 during installation
UUID=b90caa5b-79b1-4125-a542-b32eba88a1df /home           ext3    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=5b6e144c-5e1c-4236-b432-ccb1c5b159a5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```


What am I missing here?

Thanks in advance!

---

### Post by lsutiger on 2013-10-25
Had to sett user_xattr on the /home partition, not on the / as the instructions stated

---

