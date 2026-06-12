---
title: "problem moving files"
date: 2007-10-03
forum: General Help
---

### Post by Sjovan on 2007-10-03
hey, the thing is that i don't want wine and crossoveroffice to use a lot of space on my home partition. So i thought i would make a folder /mnt/c:/ and link it to /drive_c/ in .wine and .cxoffice.

I didn't have any problem moving the wine stuff, but this is what happend when i tryed it with cxoffice:
```
root@analplugg:/# mv /home/sjovan/.cxoffice/win98/drive_c/* /mnt/c\:/
mv: inter-device move failed: `/home/sjovan/.cxoffice/win98/drive_c/Program Files' to `/mnt/c:/Program Files'; unable to remove target: Is a directory

```

[solved]
all i had to do was cp it and rm it manualy. now everything works like a charm

---

