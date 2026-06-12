---
title: "GRUB Error 22: No such partition"
date: 2007-02-03
forum: General Help
---

### Post by aiv on 2007-02-03
After i restored a windows partition with Paragon my grub is gone. When i start the grub setup from a live-cd, it says:
> grub> find /boot/grub/stage1 (hd0,6)

grub> root (hd0,6) Filesystem type is reiserfs, partition type 0x83

grub> setup (hd0) Checking if "/boot/grub/stage1" exists... yes Checking if "/boot/grub/stage2" exists... yes Checking if "/boot/grub/reiserfs_stage1_5" exists... yes Running "embed /boot/grub/reiserfs_stage1_5 (hd0)"... 18 sectors are embedded . succeeded Running "install /boot/grub/stage1 (hd0) (hd0)1+18 p (hd0,6)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition

i attach my fstab and menu.lst

---

