---
title: "transparent filesystem compresion"
date: 2006-09-09
forum: General Help
---

### Post by NESFreak on 2006-09-09
what filesystem should i use when i want to compres my data without noticing it (well exept of cource for the more space availeble thing and a small preformance drop, wich i thing my 1800mhz athlon xp is perfectly able to handle.) It does need to support unix rights and stuff ofcource.

NESFreak

---

### Post by NESFreak on 2006-09-09
well i guess ZFS would be perfect. But is there already a linux implementation for it?

---

### Post by Cynical on 2006-09-09
No, someone is working on it for Google's Summer of Code. It probably won't be done for months.

---

### Post by mips on 2006-09-20
ZFS will run in userspace on Linux due to license incompatibilities as far as i can tell. BSD people will probably have better luck.

[http://www.wizy.org/wiki/ZFS_on_FUSE](http://www.wizy.org/wiki/ZFS_on_FUSE)
[http://zfs-on-fuse.blogspot.com/](http://zfs-on-fuse.blogspot.com/)

---

