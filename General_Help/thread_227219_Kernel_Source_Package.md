---
title: "Kernel Source Package?"
date: 2006-08-01
forum: General Help
---

### Post by Cath0de on 2006-08-01
So I'm trying to re-install my wireless drivers and I seem to have found a hitch. The installation readme indicates that the "compiled kernel sources or headers against the matching kernel." It tells me I need to "install the kernel source packages."

What does that mean?

---

### Post by Ramses de Norre on 2006-08-01
This should do the trick:```
sudo aptitude install linux-kernel-headers linux-headers-`uname -r`
```

---

