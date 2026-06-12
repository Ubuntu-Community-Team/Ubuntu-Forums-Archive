---
title: "Error on boot screen"
date: 2023-01-09
forum: General Help
---

### Post by shabbir23aa on 2023-01-09
2.5290301 systemd-fstab-generator [240]: Failed to create unit file /run/systemd/generator/swapfile.suap, as it already exists. Duplicate entry in /etc/fstab? 2.5434171 systemd[241]: /usr/lib/systemd/system generators/systemd-fstab-generator failed with exit status 1.


[B]cat /etc/fstab 

[/B]
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
UUID=0901bd7b-419d-4f37-929f-32b99af5932a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=1F1A-AD81  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
/swapfile none swap sw 0 0

I have increased my swap space and on reboot got this error. how to do I solve this error??

---

### Post by yancek on 2023-01-09
The error indicates an attempt to create a new swap file when one already exists and your fstab entry shows the same.  You might do an online search on the correct process on your version of Ubuntu.

 [https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-20-04)

---

### Post by MAFoElffen on 2023-01-09
As noted by 'yancek' the second entry is a duplicate, so: 
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
UUID=0901bd7b-419d-4f37-929f-32b99af5932a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=1F1A-AD81  /boot/efi       vfat    umask=0077      0       1
# /swapfile                                 none            swap    sw              0       0
/swapfile none swap sw 0 0

```
Check via
```

awk '{print $0}' /proc/swaps

```

---

