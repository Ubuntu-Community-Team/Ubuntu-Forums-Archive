---
title: "copy ubuntu without gparted's copy"
date: 2008-06-30
forum: General Help
---

### Post by jnw222 on 2008-06-30
i plan to copy my ubuntu partition to another disk, but i do not trust gparted to do it.

is there another way to do it?

---

### Post by jnw222 on 2008-06-30
link copy all files and remount partitions

---

### Post by drs305 on 2008-06-30
> **jnw222 said:**
> i plan to copy my ubuntu partition to another disk, but i do not trust gparted to do it.

is there another way to do it?

There is partimage, which makes copies of partitions. It would leave your original partition intact and can reproduce it on another drive. An advantage of partimage is that it copies all the data but does not include empty space - so a 30GB partition "image" may only take up 10GB space. I think gparted may be able to copy a partition as well, so if you don't trust it you may not want partimage either. I've never had a problem with partimage.

---

### Post by Vivaldi Gloria on 2008-07-01
> **jnw222 said:**
> i plan to copy my ubuntu partition to another disk, but i do not trust gparted to do it.

is there another way to do it?

Have a look at the clonezilla live cd:

[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

