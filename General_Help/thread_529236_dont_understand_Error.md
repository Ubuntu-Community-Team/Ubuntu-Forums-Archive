---
title: "dont understand Error"
date: 2007-08-19
forum: General Help
---

### Post by michaelaguilar on 2007-08-19
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

that pops up when i try to do my updates

---

### Post by strabes on 2007-08-19
Run this, like it says:```
sudo dpkg --configure -a
```

Then test it by running:```
sudo apt-get update && sudo apt-get upgrade
```

---

