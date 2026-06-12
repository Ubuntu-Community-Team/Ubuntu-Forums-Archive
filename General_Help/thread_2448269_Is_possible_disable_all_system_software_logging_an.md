---
title: "Is possible disable all system software logging and change temp path ?"
date: 2020-08-05
forum: General Help
---

### Post by aug7744 on 2020-08-05
In Lubuntu 20.04 is possible have an system that not create any type of logs ? If yes also is possible disable logs from any software ?
Aldo is possible change temp path to another path example an temp folder in ramdisk ?
Thanks for reply.

---

### Post by TheFu on 2020-08-05
You can create a RAM-based file system or use an overlay file system that doesn't write to disk. When the system is shutdown, the RAM would go away.  It is very common to do this for systems running off flash storage - like a router or an embedded system.

So, yes it is possible.

---

### Post by aug7744 on 2020-08-13
Thanks.

---

