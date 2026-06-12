---
title: "Cancell MATLAB installation"
date: 2013-05-24
forum: General Help
---

### Post by broels on 2013-05-24
Hello, I stupidly decided to install MATLAB from the software center without appreciating fully what it was. Evey time I try to install something new or update any existing software, it asks be to declare the exe path, which i'm almost certain doesn't exist. Is there a way to get (Xubuntu 12.10) to just forget I ever wanted to install it?

---

### Post by Irihapeti on 2013-05-24
Can you install anything new at all, even if the error message comes up?

If so, then try this:
```
 sudo apt-get purge matlab-gdf matlab-support
```

and let us know what happens.

---

