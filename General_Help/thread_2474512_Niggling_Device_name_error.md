---
title: "Niggling Device name error"
date: 2022-05-01
forum: General Help
---

### Post by makem2 on 2022-05-01
I have 2 x 1TB M2 drives each with two partitions, using xubuntu 22.04. In the thunar Devices list one partition is showing as '473 GB Volume'. The name should be data2. How can I correct this?

My fstab is:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme1n1p5 during installation
UUID=f5900b7a-10b7-452d-8d35-05f609caf7b0 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme1n1p1 during installation
UUID=40DB-4F92  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/nvme1n1p6 during installation
UUID=e225fd55-cbcb-404b-ac66-27db01e75f91 /home           ext4    defaults        0       2
# swap was on /dev/nvme1n1p8 during installation
UUID=4ede3f10-e290-4fe4-970a-27537f3a0499 none            swap    sw              0       0


#ntfs_games
UUID=6F84951F5D97E1A6   /media/makem/ntfs_games       ntfs      defaults        0       2


#data2
UUID=1c245acf-a7f1-40a5-9f3a-b5d34f03ee43       /media/makem/data2      ext4    defaults        0       2


#data
UUID=404338594EF4A720   /media/makem/data      ntfs    defaults        0       2


#windows
UUID=CE6CDDE46CDDC77D   /media/makem/Windows    ntfs    defaults        0       2

```

Devices as listed in thunar:

Files System
data
Windows
ntfs_games
473 GB Volume

---

### Post by &amp;KyT$0P# on 2022-05-01
Probably the filesystem has no label.  Try unmounting that partition, then use GParted to give it a filesystem label "data2".

---

### Post by makem2 on 2022-05-01
> **halogen2 said:**
> Probably the filesystem has no label.  Try unmounting that partition, then use GParted to give it a filesystem label "data2".

Thank you, that worked well. It also fixed that the partition was owned by me and in my group. It is now owned by root and in the root group.

---

