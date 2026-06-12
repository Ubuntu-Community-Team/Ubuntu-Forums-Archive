---
title: "Synaptic Package Manager problem :("
date: 2007-08-04
forum: General Help
---

### Post by baz.g on 2007-08-04
everything 'was' working fine and then today i tried to open synaptic package manager and i get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

so i opened terminal and pasted that command in and got this error:

dpkg: requested operation requires superuser privilege

:(

somebody please help meee :)

many thanks in advance,

Baz

---

### Post by taurus on 2007-08-04
```
**sudo** dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by baz.g on 2007-08-05
thanx very much for your help mate, that worked a treat! :)

---

