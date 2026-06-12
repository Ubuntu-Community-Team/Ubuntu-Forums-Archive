---
title: "SDL and libstdc++.so.6"
date: 2005-09-12
forum: General Help
---

### Post by Xenobia_Omega on 2005-09-12
Hey everyone.

Currently I'm working on a few programs using the SDL library from libsdl.org and I'm running into a problem. It won't run any program because it cannot find the file libstdc++.so.6 file, which is no where on the file system that I can see.

Is there anyway that I can fix this?

Thanks!

---

### Post by arnieboy on 2005-09-13
[QUOTE=Xenobia_Omega]Hey everyone.

Currently I'm working on a few programs using the SDL library from libsdl.org and I'm running into a problem. It won't run any program because it cannot find the file libstdc++.so.6 file, which is no where on the file system that I can see.

Is there anyway that I can fix this?

Thanks![/QUOTE]
do a
```
sudo apt-get install libstdc++6
```

---

