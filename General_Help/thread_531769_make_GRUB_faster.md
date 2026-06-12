---
title: "make GRUB faster"
date: 2007-08-21
forum: General Help
---

### Post by chanman on 2007-08-21
is there anyway to make make GRUB boot faster? I optimized my startup process for Ubuntu, Seems like the only thing left is GRUB. I have auto select for 2 sec, profiled the boot process, and changed the init script thingy (forget where :confused:) to "shell"

---

### Post by baklava on 2007-08-21
What filesystem are you using? When I used reiser I noticed it took forever for grub to boot ubuntu.

---

### Post by chanman on 2007-08-22
using ext3

---

### Post by kellemes on 2007-08-22
It does a long time before Grub shows?
Or it takes too long before Grub responses to your selection?

---

