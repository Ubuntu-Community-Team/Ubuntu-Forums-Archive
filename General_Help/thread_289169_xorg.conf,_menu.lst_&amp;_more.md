---
title: "xorg.conf, menu.lst &amp; more ?"
date: 2006-10-30
forum: General Help
---

### Post by rfruth on 2006-10-30
Thanks to my recent upgrade to Edgy I learned about /etc/X11/xorg.cong and /boot/grub/menu.lst, what other system files should I familiarize myself with :rolleyes:

---

### Post by bsussman on 2006-10-30
Ohboy is that a big question!

You might start by going to the /etc/init.d directory and examining the startup scripts.

/etc/default and /etc/otherdirectories contain important config info for many of the important subsystems

/var/log has you system and other logs.

your home directory containd many config files, usually hidden (.this , .that, .theother).  e.g. the .gnome2 tree has config and state info for many of the gnome bits.  .kde likewise for kde

Perhaps you should start with the question 'Which subsystems do I want to know about?'

BTW the standard for what is where is kept at [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/) but beware - it is not always followed...

---

### Post by jc87 on 2006-10-30
**/etc/apt/sources.list**

This is a big one because is where apt-get is told where to get the software when you do a **apt-get install**.

Learn to add / comment / remove repositorios to that file and you will **LOVE** Ubuntu

---

### Post by CatKiller on 2006-10-30
**/etc/fstab**

The **f**ile**s**ystem **tab**le that ties storage devices to their mount points in the filesystem tree.

---

### Post by rfruth on 2006-10-31
I've got my work cut out for me, thanks !

---

