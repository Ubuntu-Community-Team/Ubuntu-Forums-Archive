---
title: "What happened to my fstab?"
date: 2006-12-22
forum: General Help
---

### Post by rekahsoft on 2006-12-22
Hi today i was at a friends house and was looking at a his fstab and am confused with having UUID. What is this and how do i use it to load partitions? What happened to the simple device name (ex. /dev/hda1). Thanks.

---

### Post by raul_ on 2006-12-22
[http://en.wikipedia.org/wiki/UUID]("http://en.wikipedia.org/wiki/UUID")

i don't use UUID though

---

### Post by anaconda on 2006-12-22
> **rekahsoft said:**
> Hi today i was at a friends house and was looking at a his fstab and am confused with having UUID. What is this and how do i use it to load partitions? What happened to the simple device name (ex. /dev/hda1). Thanks.

/dev/hda1 still works.
and if you want a listing which has both of them (and shows which is which) just type:
ls -la /dev/disk/by-uuid

UUID is more unique, so every device has its own UUID. The problem with UUID is that it changes when you format the partition.

---

### Post by ScottMorris on 2006-12-22
I have found that the old style still works.  When I rebooted what we had changed worked and so it must have been a fluke.  Odd.

---

### Post by rekahsoft on 2006-12-22
> **anaconda said:**
> /dev/hda1 still works.
and if you want a listing which has both of them (and shows which is which) just type:
ls -la /dev/disk/by-uuid

UUID is more unique, so every device has its own UUID. The problem with UUID is that it changes when you format the partition.

Thanks :)

---

