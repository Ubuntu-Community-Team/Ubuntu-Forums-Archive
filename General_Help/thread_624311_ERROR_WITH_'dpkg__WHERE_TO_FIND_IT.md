---
title: "ERROR WITH 'dpkg  WHERE TO FIND IT?"
date: 2007-11-26
forum: General Help
---

### Post by godoftheweird334455 on 2007-11-26
Hello im quite noob in linux and i installed Ultimate Ubuntu 1.5, i was trying to install the packages for "looking glass" and then my laptop crashed sudenly, i restart it and everything works fine just when i try to install anything through any compiler or package an error meesage appears and it says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

How could i find that "dpkg" thing and how to fix it then?btw, neither the updates can ber installed.
could somebody help me or give me a link where to find a solution?

Thank you for reading:KS

---

### Post by erfahren on 2007-11-26
```

sudo dpkg --configure -a

```
(it means that literally)

---

### Post by erfahren on 2007-11-26
Oh, I should mention - don't use more that one package manager at a time (don't have Synaptic open when installing or updating through the terminal for instance).

---

