---
title: "Error message with Update Manager"
date: 2008-02-29
forum: General Help
---

### Post by kiroro on 2008-02-29
Every time I run update manager, a pop-up window tells me: 'Not all updates can be installed', 'Partial Upgrade' etc. When I click 'Check' for new updates, an error message shows:

'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I install updates, it gives me error too. So I run 'sudo dpkg --configure -a', it shows error as well. Then I tried  'sudo apt-get update', it also gives me 'dpkg was interrupted'. What problem is that? Thanks for your help!

---

### Post by zvacet on 2008-03-01
```
sudo apt-get -f install
```

---

### Post by kiroro on 2008-03-09
> **zvacet said:**
> ```
sudo apt-get -f install
```

It doesn't work. 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

---

