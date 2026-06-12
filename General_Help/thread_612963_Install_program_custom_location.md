---
title: "Install program custom location"
date: 2007-11-14
forum: General Help
---

### Post by B-Con on 2007-11-14
I have a non-administrative account on my school computers (running Ubuntu 6.06), meaning that I can't install any programs. But I'd still like to be able to use applications like KolourPaint. Is there a way to use some type of wrapper to "install" a program but not have it install to the directories I'm forbidden from writing to?

---

### Post by taurus on 2007-11-14
You can build it from source but tell it to where to install while you run the ./configure.

```
./configure --PREFIX=/where_you_want_to_install
```

---

