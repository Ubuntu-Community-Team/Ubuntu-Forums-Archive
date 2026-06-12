---
title: "grub again"
date: 2008-04-15
forum: General Help
---

### Post by nonewmsgs on 2008-04-15
i can boot from any disk.  i have 4 disks.  i cannot get as far as a grub menu (then i can fudge the numbers around and fix it).  here is a list of hard drives and what they do when booted.

sata 2 grub error 22
sata 4 flashing cursor in upperleft, but the system is unresponsive.  i have tried ctrl alt f1, etc
sata 6 starts windows (without a grub menu)
pata 0  grub error 17

---

### Post by Diabolis on 2008-04-16
reinstall grub, while at grub menu press c then follow this:

```

find /boot/grub/stage1    It will find all the places **from where** you can install grub.
root (hd?,?)              Select **from where** you want to install grub
setup (hd?)               Select the drive **in which** you want to reinstall grub
reboot
```

---

