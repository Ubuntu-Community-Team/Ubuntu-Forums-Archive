---
title: "Ubuntu 18 hibernate (resume) not working Dell XPS 13"
date: 2018-08-30
forum: General Help
---

### Post by fourhendrik on 2018-08-30
Hello,

sudo systemctl hibernate

..seems to work, but resume doesn't. boot ends up at regular login. When I try pm-hibernate, I can see this in /var/log/kern.log

Aug 30 17:22:31 xps-laptop kernel: [ 1060.483313] PM: Starting manual resume from disk
Aug 30 17:22:31 xps-laptop kernel: [ 1060.483403] PM: Image not found (code -22)
Aug 30 17:22:31 xps-laptop kernel: [ 1060.544839] PM: hibernation entry

swap is a file

hgreving@xps-laptop:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p3 during installation
UUID=870922c8-8764-446b-895c-2b7a63e5654d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=C218-2986  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

Anybody seen this?

---

