---
title: "Package Problems"
date: 2008-05-09
forum: General Help
---

### Post by nitrokid759 on 2008-05-09
When I try to install updates or Flashplayer I get this message:
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



How do I fix this?
I'm on Ubuntu 8.04 LTS

---

### Post by scragar on 2008-05-09
run```
sudo dpkg --configure -a
```from a terminal.

---

### Post by didooofidooo on 2008-05-09
just run "dpkg --configure -a" then run the command again

---

