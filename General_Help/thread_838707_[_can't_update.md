---
title: ":[ can't update"
date: 2008-06-23
forum: General Help
---

### Post by nickiegee on 2008-06-23
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

everytime i try to update ubuntu that error pops up
:/ anyone know what to do?

---

### Post by Rocket2DMn on 2008-06-23
open a terminal (Applications->Accessories->Terminal) and run
```
sudo dpkg --configure -a
```
That will get you going again.

---

### Post by brian_p on 2008-06-23
> **nickiegee said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

everytime i try to update ubuntu that error pops up
:/ anyone know what to do?

```
sudo dpkg --configure -a

```

in a terminal didn't do anything?

---

### Post by bijeeshvs on 2008-06-23
go to"applications=>accessories=>terminal"
enter "sudo dpkg --configure -a" without quotes
when its finished try updating

---

