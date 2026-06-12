---
title: "[SOLVED] Kernel install interrupted now package manager is messed up"
date: 2007-08-09
forum: General Help
---

### Post by Super TWiT on 2007-08-09
I was trying to install a custom kernel image I made myself, however it was interrupted and now when ever I try to launch any kind of package manager it says ```
E: The package linux-image-2.6.22 needs to be reinstalled, but I can't find an archive for it.
```

I have the kernel image but when I try to install it the package manager says it must be corrupted.

---

### Post by Super TWiT on 2007-08-09
Anybody?

---

### Post by Super TWiT on 2007-08-09
I was able to fix it by using APTonCD, adding the Linux image to it, and then adding the CD as a repository.  This might not have been the best way to fix it, but at least it works!

---

