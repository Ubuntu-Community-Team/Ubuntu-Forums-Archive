---
title: "kernel"
date: 2005-08-01
forum: General Help
---

### Post by leverknight1 on 2005-08-01
what kernel updates should be done to an out of the box ubuntu x86 install if any?

---

### Post by adwait on 2005-08-01
Try:
```
sudo apt-get update
sudo apt-get upgrade

```

This will upgrade everything to the latest version.l

---

### Post by az on 2005-08-01
If you have an intel processor, install the 686 kernel.  If you have a recent amd processor, install the k7 kernel.  This gives you an optimised kernel.

---

