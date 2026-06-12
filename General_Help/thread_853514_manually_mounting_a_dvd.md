---
title: "manually mounting a dvd"
date: 2008-07-08
forum: General Help
---

### Post by badfish591 on 2008-07-08
what is the argument, from terminal to manually mount a dvd as iso9660?
thought i knew but i cant get it to mount.

---

### Post by pofigster on 2008-07-08
```
mount /dev/sr0 /mnt/tmp/ -t iso9660 -o ro
```
That should work.  Of course, change the location of your device and the mounting location to match what you're actually doing.

---

### Post by badfish591 on 2008-07-08
that did man, thanks.

---

