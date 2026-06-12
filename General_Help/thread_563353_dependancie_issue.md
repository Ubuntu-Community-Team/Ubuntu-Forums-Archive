---
title: "dependancie issue"
date: 2007-09-29
forum: General Help
---

### Post by searayman on 2007-09-29
I am trying to install webrunner, but i get this wen tryign to run it:

./webrunner: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

any ideas?

---

### Post by tbroderick on 2007-09-29
Installing libstdc++5 comes to mind.

---

### Post by Sef on 2007-09-30
> Installing libstdc++5 comes to mind.

From the Terminal:

```
sudo aptitude update
```

```
sudo aptitude install libstdc++5
```

---

