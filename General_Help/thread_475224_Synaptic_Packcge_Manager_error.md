---
title: "Synaptic Packcge Manager error"
date: 2007-06-15
forum: General Help
---

### Post by Scubs on 2007-06-15
When ever I open Synaptic Package Manger, I get an error. Which says the following

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried running 'dpkg --configure -a' in terminal, but it said 

Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: --configure
bash: dpkg --configure -a: command not found


Any help would be grateful

thanks

---

### Post by zvacet on 2007-06-16
```
sudo dpkg --configure -a
```

---

