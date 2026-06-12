---
title: "Finding all corrupted rar archives"
date: 2017-03-04
forum: General Help
---

### Post by kopi23 on 2017-03-04
Hi, is there a way to check _all_ parts of a rar archive for corruption?
unrar t *.rar stops after the first corrupted rar.
Thanks, kopi

---

### Post by howefield on 2017-03-04
Possibly...

```
unrar t nameofile.rar
```

---

### Post by kopi23 on 2017-03-04
unfortunately if i have a splited archive (foo.part01.rar, foo.part02.rar, ...) this doesn't work. if i try it like unrar t foo.part02.rar, it starts with the first part and stops at the first corrupted file.

---

