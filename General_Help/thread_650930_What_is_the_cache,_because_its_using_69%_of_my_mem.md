---
title: "What is the cache, because its using 69% of my memery"
date: 2007-12-27
forum: General Help
---

### Post by hhhhhx on 2007-12-27
Yes, i know im still a noob, but what is the cache and how do i make it stop using so much RAM

thankfully
xhhux

---

### Post by chewearn on 2007-12-27
> **xhhux said:**
> Yes, i know im still a noob, but what is the cache and how do i make it stop using so much RAM

thankfully
xhhux

It not important to free up the cache.  It just the way Linux works.

The cache is storing data/application/etc, so that next time you access it, it don't need to access the slower harddisk.

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by hhhhhx on 2007-12-27
so will it slow down my com?

---

### Post by dashnak on 2007-12-27
No, on the contrary, it will speed it up....

---

### Post by hhhhhx on 2007-12-27
> **dashnak said:**
> No, on the contrary, it will speed it up....
  ok that realy make no sence, but if it doesent slow it down, i dont care :guitar:

---

### Post by t3hi3x on 2007-12-27
You should think of it as reserving the memory until its needed. It just speeds up the process of getting things to the memory. Also makes it where it doesn't have to overflow into the virtual memory (swap) which is much much slower than RAM.

Does this help?

---

### Post by hhhhhx on 2007-12-27
yep thanks a lot

---

### Post by terminal on 2007-12-27
Unlike windows xp linux tries to utilize all the free ram it can to cache files/application and speed up usage . In Xp if you have 2 gb ram, then u can see it hardly uses 512 mb and rest is as it is . Windows Vista also has  superfetch which tries to utilize free ram by using it to cache frequently used programs .

---

