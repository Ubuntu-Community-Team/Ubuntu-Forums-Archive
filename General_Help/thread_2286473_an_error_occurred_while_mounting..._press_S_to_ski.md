---
title: "an error occurred while mounting... press S to skip or M for manual recovery"
date: 2015-07-12
forum: General Help
---

### Post by petermartin2 on 2015-07-12
Could anyone tell me what I should do? I'm a newbie but I managed to dig out my fstab it looks like this:

```
 # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=6e854bed-41d2-4065-b3a4-1ac64631bfac /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda3 during installation
UUID=E3EF-161F  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda2 during installation
UUID=4609c5ca-6371-4e30-a817-f25115097b18 none            swap    sw              0       0
/dev/disk/by-uuid/e003167f-94d2-4d50-a60a-86eb6a91878f /mnt/e003167f-94d2-4d50-a60a-86eb6a91878f auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/3ec4bcbc-7da0-4bd7-8bb3-a5ad79059173 /mnt/3ec4bcbc-7da0-4bd7-8bb3-a5ad79059173 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/b9d026d4-6d42-4685-8d9d-47b295a04ff2 /mnt/b9d026d4-6d42-4685-8d9d-47b295a04ff2 auto nosuid,nodev,nofail,x-gvfs-show 0 0
```

---

### Post by ajgreeny on 2015-07-12
Where did those three final lines come from?
```
/dev/disk/by-uuid/e003167f-94d2-4d50-a60a-86eb6a91878f /mnt/e003167f-94d2-4d50-a60a-86eb6a91878f auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/3ec4bcbc-7da0-4bd7-8bb3-a5ad79059173 /mnt/3ec4bcbc-7da0-4bd7-8bb3-a5ad79059173 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/b9d026d4-6d42-4685-8d9d-47b295a04ff2 /mnt/b9d026d4-6d42-4685-8d9d-47b295a04ff2 auto nosuid,nodev,nofail,x-gvfs-show 0 0
``` Have you any idea what partitions or devices attached to your computer they relate to?

Show us the exact error message if you can, even a camera shot if needed, as we can not tell you what to do without knowing which partitions are throwing that error.

Also show us the output of ```
sudo blkid -c /dev/null
```

---

### Post by yancek on 2015-07-12
The most common reason for seeing that message in my experience is if there is an entry in the fstab file for a partition or partitions on an external disk which is NOT attached at boot.

---

### Post by Bucky Ball on 2015-07-12
> **yancek said:**
> The most common reason for seeing that message in my experience is if there is an entry in the fstab file for a partition or partitions on an external disk which is NOT attached at boot.

Makes sense. Maybe external drives were attached during installation which are not attached now? Just a thought. :-k

@petermartin2: It should be quite fine/safe to hit 'S' to skip the errors and boot on to fix it up. Just tells the system to ignore trying to mount the partitions it can't find. :)

---

