---
title: "Uninstalling Audacity beta if Tarball is deleted?"
date: 2007-09-02
forum: General Help
---

### Post by MCrittenden on 2007-09-02
I'm on Audacity 1.3.3 (the beta...not from the repos) and somehow deleted the tarball and all of the extracted files. Is there any way to uninstall now? Everything I can find says that the only way to uninstall .tar.gz files is to navigate to the directory and run "sudo make uninstall" ...so what if the directory doesn't exist anymore?

Be gentle....I'm a noob.

I'm on 7.04 (Feisty).

---

### Post by MCrittenden on 2007-09-04
Just a bump. Anyone? It has to be an easy solution.

---

### Post by cwaldbieser on 2007-09-05
> **MCrittenden said:**
> Just a bump. Anyone? It has to be an easy solution.

Can you just get the tarball and build it again?  Then you can uninstall it with make uninstall.
Also, when building from source, if you use "checkinstall", it integrates with the packaging system so you don't run into this problem.

---

### Post by MCrittenden on 2007-09-05
I knew it was simple. Thanks!

---

