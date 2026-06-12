---
title: "Synaptic Error"
date: 2007-06-23
forum: General Help
---

### Post by init1 on 2007-06-23
E: /var/cache/apt/archives/xpuyopuyo_0.9.8-3_i386.deb: failed to unlink `/var/lib/dpkg/tmp.ci'
No matter what I try to install with apt/synaptic, I get 
failed to unlink `/var/lib/dpkg/tmp.ci'

---

### Post by r0ck80y on 2007-06-24
Remove that directory manually
```
 rm -rf /var/lib/dpkg/tmp.ci
```
Then run apt.

---

