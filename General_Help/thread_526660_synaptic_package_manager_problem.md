---
title: "synaptic package manager problem"
date: 2007-08-15
forum: General Help
---

### Post by seebedoubleyou on 2007-08-15
it was working fine but now when i go to open the synaptic package manager it says this



E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


i don't know what to do to make it work again

---

### Post by EXCiD3 on 2007-08-15
Open terminal and type:```
dpkg --configure -a
```

---

### Post by zvacet on 2007-08-15
```
sudo dpkg --configure -a
```

---

### Post by seebedoubleyou on 2007-08-15
thanks 

i had to login into root to do it though

everything is fixed now

---

