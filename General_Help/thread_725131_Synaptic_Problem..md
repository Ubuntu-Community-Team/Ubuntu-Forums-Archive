---
title: "Synaptic Problem."
date: 2008-03-15
forum: General Help
---

### Post by xVehemencityx on 2008-03-15
I can't seem to use synaptic.  I'm sure it was something I did, but I dunno how to fix it.  Whenever I open it, it says ```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```  Any ideas?

---

### Post by taurus on 2008-03-15
Close synaptic.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

---

