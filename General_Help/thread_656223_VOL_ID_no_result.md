---
title: "VOL_ID no result"
date: 2008-01-02
forum: General Help
---

### Post by eskimo on 2008-01-02
Hi, after installing a new hard disk (that became the second, in a preexistent 3 hard disks system) and installing windows xp on it, i noticed bad errors on UUID of my first hard disk, the one with my root, my home and swap partition (respectively sda1 sda3 sda2)

i saw that problems camed out from UUID, in fact writing /dev/sda1 in fstab it worked. So now i have this problem:
sudo vol_id -u /dev/sda1    doesn't return anything!!! while launching the command on sda2, sda3 and other partitions of others hard disk returns me the right UUID!!!
what can i do?
thank you...
Paolo

---

### Post by eskimo on 2008-01-03
no one has an answer? maybe i didn't explain my problem clearly.... i can't get a result from a 
vol_id -u /dev/sda1  (my root partition)

anyone knows why?

---

### Post by iris-n on 2008-01-04
I'm not sure i understood you.
Your system is working or not?
Which problems do you have?

Anyway, if you removed the UUID from fstab wouldn't it just not exist anymore?
I'm no expert in them, but from what i've read you can use /dev/sdXY instead without (much) problem.

What i understand is, UUID is used to uniquely identify partitions regardless of mount point and node.

One thing that could generate a problem at boot is a mismatch of UUID between /boot/grub/menu.lst and /etc/fstab.

Hope it is of any help.

---

