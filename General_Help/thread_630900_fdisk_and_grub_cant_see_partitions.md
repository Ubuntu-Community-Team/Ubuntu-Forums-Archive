---
title: "fdisk and grub cant see partitions"
date: 2007-12-03
forum: General Help
---

### Post by tux crasher on 2007-12-03
Hey, I data dumped vista from /dev/sda0 to /dev/sdb3 and grub cant see /dev/sdb3 for some reason. i also ran fdisk -l and it shows all the partitions under sda but none  under sdb. all the sdb partitions were made under vista, does that have something to do with it? or does anyone know how to fix this? i can mount partitions on sdb.
thanks
m

---

### Post by mozkill on 2007-12-03
its hard to understand what you are doing.  did you set the bootable flags correctly?  did you reboot after changing the partition table?

---

### Post by teryowen on 2007-12-03
Its prolly because vista paritioned your other hard drive and i hear it has something to do with different types of paritions tables not sure.

---

