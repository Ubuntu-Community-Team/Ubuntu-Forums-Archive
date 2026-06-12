---
title: "Let's mount a hard drve! Or not."
date: 2008-07-09
forum: General Help
---

### Post by scuminex on 2008-07-09
ok. So, I've been running hardy 8.04 on a dell ins6xxx,2Ghz ic. Bought an external that seemed to have been working flawlessly until I copied some stuff to it from a buddy of mine, who is running hardy. Ever since, I try opening it only to find that " the drive can not be mounted. Try this instead.........." I followed the directions on prior post concerning it to no avail. Any help would be greatly appreciated. Take care. -A

---

### Post by VMC on 2008-07-09
> **scuminex said:**
> ok. So, I've been running hardy 8.04 on a dell ins6xxx,2Ghz ic. Bought an external that seemed to have been working flawlessly until I copied some stuff to it from a buddy of mine, who is running hardy. Ever since, I try opening it only to find that " the drive can not be mounted. Try this instead.........." I followed the directions on prior post concerning it to no avail. Any help would be greatly appreciated. Take care. -A

So ubuntu works. It's just when you plug in your external drive, you can't mount it , correct?
 From a Terminal and with the external drive plugged in type:

```
sudo fdisk -l
```

---

### Post by un_dave on 2008-07-09
I've had issues like this with NTFS formatted drives too. Generally it occurs when you disconnect the drive from a windows pc without "Safely Removing Hardware". Somehow the drive then gets flagged as dirty, and the NTFS handler in ubuntu doesn't want to touch a dirty drive, just in case it breaks it.

In this situation, I've never had any issues with following the command listed in the warning message, however if this doesn't work, I'd say the simplest thing would be to plug it back into a Windows machine, run a chkdsk on the drive, and then safely disconnect it. This should remove the dirty flag on the disk, and it should be fine next time you plug it into ubuntu.

---

