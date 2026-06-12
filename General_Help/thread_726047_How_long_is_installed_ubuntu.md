---
title: "How long is installed ubuntu"
date: 2008-03-16
forum: General Help
---

### Post by Michalxo on 2008-03-16
Hello, is there any command to find out how long do I have installed my system? I think I saw it somewhere, but I dont remember now, can you help me freshem my memory? thx

---

### Post by jimbren on 2008-03-16
```
ls -l /vmlinuz
```
should do the trick.

The date on the file would be the date you installed the system.

---

