---
title: "Synaptic Problem!"
date: 2007-07-07
forum: General Help
---

### Post by Prima Facie on 2007-07-07
When I open Synaptic, I get this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

How can this be corrected?

---

### Post by taurus on 2007-07-07
Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

