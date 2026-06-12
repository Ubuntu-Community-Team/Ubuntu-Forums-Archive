---
title: "problem with libc"
date: 2008-02-23
forum: General Help
---

### Post by gleery on 2008-02-23
I've just install a simplified version of ubuntu, I tried to compile a simple c program, but 
got gcc complaints: can't find stdio.h and also unable to find crtXX.o. 
   I've tried apt-get install libc6, which tells me I've got a latest version of it.
   I didn't see any c header files in /usr/include/, does this mean they are missing? If yes, what should I do?

---

### Post by taurus on 2008-02-23
Before you attend to compile or build anything from source, you need to install the build-essential package first.  That would take care of that stdio.h and others.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

