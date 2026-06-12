---
title: "mc in console mode garbled"
date: 2008-03-12
forum: General Help
---

### Post by kriukov on 2008-03-12
Due to some reason mc in console mode looks garbled (please see the picture attached). I remember having this problem before and it seems like it had something to do with libc6 and depended on the type of hardware (on some machines it was present, on some not). Does anyone know how to fix it?

---

### Post by kerry_s on 2008-03-12
make sure you set the right screen size in your boot line " vga=? ", i use "vga=791" for 1024x768.

---

### Post by kriukov on 2008-03-16
Thank you, I just restored the partition from the backup image file and it was all right. But I've had this problem on several machines, so I am going to check that option. I guess in the default menu.lst it is altogether absent.

---

