---
title: "cant reinstalll grub after windows"
date: 2008-06-01
forum: General Help
---

### Post by boyce1 on 2008-06-01
ok, so i was previously dual-booting and it was working perfect. however, i messed up windows and had to reinstall it. i went into gparted, deleted the ntfs partition and then reinstalled windows on the empty space.

Windows boots fine,  but i have to reinstall grub to allow me to also boot into linux.

from a livecd, i try to install grub, but stage2 seems to fail.
[B]
grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested[/B]

Also, in the gparted cd, i cant find anypartitions, just 232gb of unnalocated space :(

please help :)

---

### Post by didac on 2008-06-02
Do the following:

```
sudo grub

find /boot/grub/stage2

```

It will answer where stage2 is located. Choose it as root

---

