---
title: "unable to fine stdio.h"
date: 2007-11-12
forum: General Help
---

### Post by umasadan on 2007-11-12
during compiling C program unable to locate stdio.h...
trying to install xine-lib-1.1.7 got error cannot create executable

---

### Post by taurus on 2007-11-12
You need the build-essential package.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install build-essential
gcc -v
```

---

