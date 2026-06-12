---
title: "Tried to install limewire, keep getting error msgs now"
date: 2007-06-21
forum: General Help
---

### Post by valoteagan on 2007-06-21
I tried to install limewire but it locked up while installing, i rebooted and tried again but then got this error msg
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

now i keep getting this while doing various thing like running update manager

any help to solve this would be appriciated

---

### Post by The Wisedude on 2007-06-21
> **valoteagan said:**
> I tried to install limewire but it locked up while installing, i rebooted and tried again but then got this error msg
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

now i keep getting this while doing various thing like running update manager

any help to solve this would be appriciated



Try typing 
 dpkg --configure -a

In the terminal

---

### Post by NeoLithium on 2007-06-21
open up a terminal window (Applications -> Accessories -> Terminal) and type in:
```
sudo dpkg --configure -a
```

It requires root permissions to use dpkg :)

---

### Post by valoteagan on 2007-06-21
thanks a lot that got it sorted

---

