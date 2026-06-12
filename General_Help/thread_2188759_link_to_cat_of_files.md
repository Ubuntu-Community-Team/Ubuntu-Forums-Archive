---
title: "link to cat of files"
date: 2013-11-18
forum: General Help
---

### Post by saurish on 2013-11-18
If I have 2 files a.dat and b.dat, is there a way to create a symbolic link file link.dat such that 
cat link.dat
will give the same output as
cat a.dat b.dat?

---

### Post by tgalati4 on 2013-11-18
I don't know of a way using *ln* directly.  You could write a script using the *tee* command:

```
man tee
```

---

