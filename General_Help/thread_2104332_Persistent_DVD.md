---
title: "Persistent DVD"
date: 2013-01-12
forum: General Help
---

### Post by msramalho on 2013-01-12
Is it possible to use a Linux Persistent DVD. I have looked everywhere and I can not find the answer.
Thanks

---

### Post by Cheesemill on 2013-01-12
No.

You can only have persistence on a block device that allows reading and writing.
Rewritable DVD's don't count as the method used for writing isn't the same as a flash drive or hard drive.

You can however create a persistence file on a USB stick to use with a Live DVD.

---

### Post by msramalho on 2013-01-12
this will allow me to save apps and documents, right?

---

### Post by msramalho on 2013-01-12
I believe this will help me with my macbook.
thanks for the quick rely

---

### Post by C.S.Cameron on 2013-01-12
You can create an ext2 partition on a usb stick and label it casper-rw.
Insert it before booting the Live CD.
When booting the Live CD press F6.
Then type <space>persistent.

```
 persistent
```

---

### Post by msramalho on 2013-01-13
thanks

---

