---
title: "Error: missing file X11/Xmu/WinUtil.h"
date: 2007-07-26
forum: General Help
---

### Post by Goombie on 2007-07-26
So, I'm trying to install the latest version of fbpanel from source. When I run make on the source code, I get the following error message:
```

CC   systray/main.o
main.c:5:29: error: X11/Xmu/WinUtil.h: No such file or directory
make[1]: *** [main.o] Error 1
make: *** [systray] Error 2

```

I did a little bit of googling, and it seems that I need to install a package, but I don't know which one. One place said to install "libxorg-x11-devel", but I couldn't find that package in Synaptic. 
Does anyone know how I can fix this? Thanks! :)

---

### Post by netimen on 2007-08-17
I met the same problem, but installing **xlibs-dev** fixed it

---

