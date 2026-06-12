---
title: "Synaptic error"
date: 2008-04-27
forum: General Help
---

### Post by Aquastus on 2008-04-27
Ok, first I wanted to install a .deb package but then it told me that only one package manager can be run at the same time, which was weird because I didn't have any other applications running. So then I wanted to open Synaptic, but it gave me this error:
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```
So, again, I don't even understand what this means and have absolutely no idea what to do.

---

### Post by ryanhaigh on 2008-04-28
Open a terminal and use ```
sudo dpkg --configure -a
```.

As for the multiple package manager issue, perhaps the update manager was running.

---

