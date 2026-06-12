---
title: "Removing a package and all related packages?"
date: 2008-04-27
forum: General Help
---

### Post by nLinked on 2008-04-27
If I installed a package from Synaptic Package Manager and it required other packages to be installed with it as dependencies, and I later decide to remove the package, how can I let it remove its original dependencies as well automatically if I don't remember them?

And on a more basic note, what is the difference between removing a package and completely removing a package? Will the latter remove it from Synaptic as well?

---

### Post by fk4n on 2008-04-27
Here is a link I found ages ago. I always use it to clean up all the unessary files.

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by kellemes on 2008-04-27
> **nLinked said:**
> If I installed a package from Synaptic Package Manager and it required other packages to be installed with it as dependencies, and I later decide to remove the package, how can I let it remove its original dependencies as well automatically if I don't remember them?

And on a more basic note, what is the difference between removing a package and completely removing a package? Will the latter remove it from Synaptic as well?

Previous poster gave a fine link..

Myself I use from commandline..
```
sudo apt-get autoremove
```
to remove unused stuff.

Packages will not be removed from synaptic.
Synaptic does nothing but show the packages made available through the repositories, this obviously includes packages you may have removed from your system.

---

### Post by nLinked on 2008-04-27
An auto-cleanup! That's great, thanks both!

---

