---
title: "Is mounting a disk twice cause issues?"
date: 2013-06-21
forum: General Help
---

### Post by thordom on 2013-06-21
Hi,

I currently have 2 hard disks mounted (LUKS encrypted as well), one of these is mounted on two different mount points.

Is that a problem?, will it cause performance issues or can it cause other issues?

The disks seem to be OK, but would like to check for 'best practice'.

Thanks

---

### Post by Grenage on 2013-06-21
While I personally wouldn't want to mount the same filesystem twice (I can't think of a single good reason to do so), it should be ok.  I suppose that any software that might be indexing stores could possibly see them as unique, and index them twice.

---

### Post by thordom on 2013-06-21
Excellent, that matched up with my thoughts as well :KS

---

