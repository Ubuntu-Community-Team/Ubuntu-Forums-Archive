---
title: "mounting issue"
date: 2007-07-13
forum: General Help
---

### Post by nate_nightroad on 2007-07-13
hey...here is my story...i got tis 80gb hdd with 3 partitions...partition A has windows in it, partition B has ubuntu and partition C is just for data storage...then yesterday i format partition C using windows..and now when i start ubuntu, the partition C is not auto mounted...is there anyway to make the partition C auto mount????

---

### Post by merlinus on 2007-07-13
Post the output of each of these terminal commands:

```

sudo fdisk -l
blkid
cat /etc/fstab

```

-merlin

---

### Post by stchman on 2007-07-13
> **nate_nightroad said:**
> hey...here is my story...i got tis 80gb hdd with 3 partitions...partition A has windows in it, partition B has ubuntu and partition C is just for data storage...then yesterday i format partition C using windows..and now when i start ubuntu, the partition C is not auto mounted...is there anyway to make the partition C auto mount????

This should help:

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

### Post by nate_nightroad on 2007-07-14
thanks problem solved

---

