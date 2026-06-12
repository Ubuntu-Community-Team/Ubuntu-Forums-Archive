---
title: "Changing the order of partitions"
date: 2006-12-21
forum: General Help
---

### Post by georgecm3 on 2006-12-21
Hello everyone,

I copied my ubuntu partition's contents onto a partition with more free space, using gparted.
Now I want to make sure that my computer boots into the new partition and not the old one. How do I do this?
Thank you in advance.

---

### Post by bodhi.zazen on 2006-12-21
You need to edit /boot/grub/menu.lst and /etc/fstab.

See if this helps:

[http://www.ubuntuforums.org/showthread.php?&t=316237](http://www.ubuntuforums.org/showthread.php?&t=316237)

---

### Post by georgecm3 on 2006-12-21
Thanks, that worked out just fine!

---

