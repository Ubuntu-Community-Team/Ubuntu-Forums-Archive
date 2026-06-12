---
title: "Grub error 22"
date: 2008-04-19
forum: General Help
---

### Post by fearpi on 2008-04-19
I had:

/dev/sda1, ntfs, Windows XP.
/dev/sda2, ext3, Ubuntu.
/dev/sda3, swap.

I changed it to:


/dev/sda1, ntfs, Windows XP.
/dev/sda2, ext3, Ubuntu.
/dev/sda4, ext3, Debian.
/dev/sda3, swap.

This was working fine. I changed it back to what it was;

/dev/sda1, ntfs, Windows XP.
/dev/sda2, ext3, Ubuntu.
/dev/sda3, swap.

I now get Grub error 22 on bootup.
Trying to repair from Ubuntu live CD proves fruitless. I can mount sda1 and sda2 and read from them with no problem. But if I run grub:

1. **root (hd0,0)** yields Error 21: Selected disk does not exist. As does root (hd0,1), root (hd0,2), root (hd1,0), etc.
2. **find /boot/grub/stage1** yields Error 15: File not found. Like I said before, I can mount the disk and see clearly the named file.

How do I reinstall grub?

---

### Post by GuitarRocker2562 on 2008-04-19
Have you tried the update-grub command on a live CD. Google to figure out how to use this command, that should help it.

---

### Post by fearpi on 2008-04-20
It didn't.

---

