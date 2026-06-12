---
title: "[SOLVED] sudo probs"
date: 2008-01-25
forum: General Help
---

### Post by craig88 on 2008-01-25
guys sorry to bother ya again but wtf does this mean 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
craig@craigs-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
craig@craigs-laptop:~$

---

### Post by craig88 on 2008-01-25
p.s i cant run any sudo commands and i get same error when i go to the synaptic pack manager

---

### Post by taurus on 2008-01-25
Close whatever window you have running like synaptic or Add/Remove.  Then, what happens when you run these commands from a terminal?

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by craig88 on 2008-01-26
the first command said this :

Setting up libc6 (2.6.1-1ubuntu10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place


and the last two just updated wine

---

### Post by craig88 on 2008-01-26
i just checked synaptics and its running fine now thanks for ur help :)

---

