---
title: "Swapoff on Wubi Lubuntu 12.10 during startup"
date: 2012-10-20
forum: General Help
---

### Post by Lyfang on 2012-10-20
Hi, I would like to disable swap on Wubi Lubuntu 12.10 during startup.

Turn off swap manually:
```
sudo swapoff -a
```

Turn on swap on Wubi Lubuntu:
```
sudo swapon /host/ubuntu/disks/swap.disk
```

gksudo leafpad /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

```
What about /etc/sysctl.conf and "vm.swappiness=0"?

Any help is greatly appreciated!

---

### Post by Lyfang on 2012-10-20
I removed the line: "/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0"

gksudo leafpad /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1

```
Before:
free -m
```
             total       used       free     shared    buffers     cached
Mem:          1749       1127        622          0        427        494
-/+ buffers/cache:        205       1544
Swap:          255          0        255

```
After:
free -m
```
             total       used       free     shared    buffers     cached
Mem:          1749       1130        619          0        431        496
-/+ buffers/cache:        201       1548
Swap:            0          0          0

```
[SOLVED] Swapoff on Wubi Lubuntu 12.10 during startup.

---

