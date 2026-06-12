---
title: "Randy"
date: 2007-12-06
forum: General Help
---

### Post by Randy Matheson on 2007-12-06
hi ... just came across an error I can't figure out ... when attempting to download updates, an error message came up as follows ...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

i tried entering dpkg--configure-a in terminal, but no luck ... any advise out there?

a newbe to ubuntu

---

### Post by taurus on 2007-12-06
Open a terminal again and run

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

