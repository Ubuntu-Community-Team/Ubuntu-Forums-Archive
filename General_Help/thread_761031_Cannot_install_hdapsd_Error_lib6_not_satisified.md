---
title: "Cannot install hdapsd Error: lib6 not satisified"
date: 2008-04-20
forum: General Help
---

### Post by Lord Xeb on 2008-04-20
?_?


```
root@xebraethus:/usr/src/linux# patch -p1 < /usr/src/linux/hdaps_protect.20060409.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -urN linux-2.6.16.original/block/ll_rw_blk.c linux-2.6.16.hdaps/block/ll_rw_blk.c
|--- linux-2.6.16.original/block/ll_rw_blk.c    2006-03-20 05:53:29.000000000 +0000
|+++ linux-2.6.16.hdaps/block/ll_rw_blk.c       2006-03-28 20:39:03.000000000 +0100
--------------------------
File to patch: 

```

What do I do here

---

### Post by Lord Xeb on 2008-04-23
I would like some help soon you know -_-. I have been working on this for almost 5 days now and still no progress

---

