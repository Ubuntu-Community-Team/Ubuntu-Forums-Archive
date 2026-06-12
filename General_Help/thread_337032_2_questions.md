---
title: "2 questions"
date: 2007-01-12
forum: General Help
---

### Post by atlfalcons866 on 2007-01-12
1.how do i remove the windows xp bootup thing in gnome. i just removed its partition

2.how do i merge windows xp old partition to the linux one? they are right next to each other?

---

### Post by jd65pl on 2007-01-12
TO remove windows from grub
```
gksudo /boot/grub/menu.lst
```
and remove its entry

You could format your old windows part and mount it on your existing system.

---

### Post by az on 2007-01-12
> **atlfalcons866 said:**
> 1.how do i remove the windows xp bootup thing in gnome. i just removed its partition

2.how do i merge windows xp old partition to the linux one? they are right next to each other?

1.  You remove it from the menu.list in /boot/grub

2.  If the first partition is bigger than the second, you boot the live cd and use gparted to move (copy) the partition there.  Then, you delete the second partition and extend the first on - don<t forget to extend the filesystem too.

You will also have to change your /etc/fstab mount points to reflect the new partition numbers.  You will have to edit the menu.list to point to the correct partitions as well.  Then, reinstall grub with the new settings.

sudo grub-install /dev/hda (if the hard drive is indeed hda)

---

