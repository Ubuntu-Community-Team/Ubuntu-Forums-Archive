---
title: "Trying to mount iso"
date: 2006-12-20
forum: General Help
---

### Post by jokr004 on 2006-12-20
Hey, I'm trying to mount an iso image in edgy.  I enter this in a root terminal

```
mount -o loop -t iso9660 px-cod3.iso /mnt/isomount/
```

and get ```
mount: Not a directory
```


Any ideas why this isn't working?

---

### Post by meng on 2006-12-20
I assume that px-cod3.iso exists in the working directory, and that /mnt/isomount already exists. Can you confirm please?

---

### Post by jokr004 on 2006-12-20
yes they do exist and the iso is in the working directory

---

