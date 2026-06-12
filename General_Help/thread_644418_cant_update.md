---
title: "cant update"
date: 2007-12-18
forum: General Help
---

### Post by cgerb on 2007-12-18
i get this msg when trying to do any updating

an error has occurred

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


not sure what to do  to get updates
thanks

---

### Post by rsambuca on 2007-12-18
You need to run the command that it tells you, but you need to use 'sudo' to attain the proper permissions.  Thus:

```
sudo dpkg --configure -a
```

---

### Post by cgerb on 2007-12-18
ahhh, still trying to get use to this command line lifestyle.  thanks for the quick reply

---

