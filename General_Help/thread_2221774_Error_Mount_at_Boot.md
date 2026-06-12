---
title: "Error Mount at Boot"
date: 2014-05-03
forum: General Help
---

### Post by rockstargroover on 2014-05-03
I'm trying to mount a few drives at boot automatically that I repartitioned.  All my data is still on these drives so repartitioning isn't an option.

Here's what I've tried.

disks > auto mount off > /dev/sdd1 
disks > auto mount off > /dev/sdb1

I'm trying to mount them where they usually do if I click on the drive in file manager.

At boot it says failed to mount, and I have the option to S Skip or M Manual recovery.

here is my fstab

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=c97ad1e1-0fc4-4b25-92de-341bde23b725 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0




/dev/sdd1 /media/r3s/Temple auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=Temple 0 0
/dev/sdb1 /media/r3s/Videos auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=Videos 0 0


---

