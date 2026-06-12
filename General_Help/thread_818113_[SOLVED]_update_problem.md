---
title: "[SOLVED] update problem"
date: 2008-06-04
forum: General Help
---

### Post by rogerzoom on 2008-06-04
While installing an update, I had a power cut! When I tried to resume the update Manager I get this message:-
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What does this mean and what must I do?

Thanks

---

### Post by lizzard on 2008-06-04
Just open a terminal and type```
sudo dpkg --configure -a
``` That should fix it.

---

### Post by rogerzoom on 2008-06-04
Thanks - seems to be running sweetly!

---

