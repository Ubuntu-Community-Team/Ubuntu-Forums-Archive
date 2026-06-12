---
title: "PSPVC compile"
date: 2008-05-23
forum: General Help
---

### Post by moribalkin on 2008-05-23
Hey they, I've been playing around with ubuntu compiling and got the pspvc installation to go, but I get this at the end:
```
install -d /usr/local/share/pspvc/bin /usr/local/share/pspvc/include
install: cannot create directory `/usr/local/share/pspvc': Permission denied
install: cannot create directory `/usr/local/share/pspvc': Permission denied
make: *** [install] Error 1

```

---

### Post by bwhite82 on 2008-05-23
You can compile a program w/o root privileges but not install it after its compiled. That's why you always do:

> make
then
> **sudo** make install

---

