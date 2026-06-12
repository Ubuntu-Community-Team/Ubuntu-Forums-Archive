---
title: "system updating problem"
date: 2008-06-27
forum: General Help
---

### Post by ekmon1582 on 2008-06-27
When I try to update my system, I get the following error;

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

Anyone know what it is, or how to fix it?

---

### Post by Vivaldi Gloria on 2008-06-27
> **ekmon1582 said:**
> When I try to update my system, I get the following error;

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

Anyone know what it is, or how to fix it?

Have you tried running

```
sudo dpkg --configure -a
```

in a terminal?

---

### Post by ekmon1582 on 2008-06-27
Nope. Worked, thank you very much.

---

