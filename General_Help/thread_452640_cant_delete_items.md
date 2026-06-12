---
title: "cant delete items"
date: 2007-05-23
forum: General Help
---

### Post by atlfalcons866 on 2007-05-23
hi i cant delete these 2 from the trash bin.

---

### Post by taurus on 2007-05-23
What are the permissions of those files in your trash bin?

Applications -> Accessories -> Terminal
```
ls -la ~/.Trash
```

---

### Post by atlfalcons866 on 2007-05-23
drwx------  4 jack jack 4096 2007-05-23 14:31 .
drwxr-xr-x 21 jack jack 4096 2007-05-23 14:53 ..
drwxr-xr-x  4 jack jack 4096 2007-04-30 00:11 ndiswrapper-1.43
drwxr-xr-x  4 jack jack 4096 2007-05-23 14:20 tew-421pc


what ever that means

---

### Post by taurus on 2007-05-23
Try

```
cd ~/.Trash
rm -rf ndiswrapper-1.43 tew-421pc
ls -la
```

---

### Post by atlfalcons866 on 2007-05-23
i used those folders for my wireless device will anything happen to the driver or anything else.

---

### Post by taurus on 2007-05-23
If you still need it, then better not remove it.  However, if you have already installed it, then you don't need th source directory anymore unless you need to recompile it or remove it.

---

