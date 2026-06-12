---
title: "[SOLVED] package manager"
date: 2008-05-05
forum: General Help
---

### Post by justborn on 2008-05-05
i have problem wid ma package manager and update manager
when ever i try to update or install any package manually ,i get this error


[COLOR="Red"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/COLOR]
and when i tried it out in the terminal i get dis

[COLOR="Red"]sudo: unable to resolve host appy-desktop
[/COLOR]
please help me!

---

### Post by vishzilla on 2008-05-05
> **justborn said:**
> i have problem wid ma package manager and update manager
when ever i try to update or install any package manually ,i get this error


[COLOR="Red"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/COLOR]
and when i tried it out in the terminal i get dis

[COLOR="Red"]sudo: unable to resolve host appy-desktop
[/COLOR]
please help me!

you need the root privilege try ```
sudo dpkg --configure -a
```

---

### Post by justborn on 2008-05-06
my porbo is rectified ,thank u for trying to help.
thread solved.

---

