---
title: "Installing manually over package manager install"
date: 2008-06-29
forum: General Help
---

### Post by Cubby on 2008-06-29
Hi,

I use the KDE desktop 3.5.8 and have k3b version 1.0.3:installed, but I noticed that it doesn't have all of the features that are listed here (there is no advanced tab in my K3b version and it doesn't have that blue skin as is posted here, as mine is rather generic looking, 

[http://forums.fedoraforum.org/forum/showthread.php?p=772752](http://forums.fedoraforum.org/forum/showthread.php?p=772752)

So, I figure that this is a newer version of k3b.

As a general question, should one remove a pre-installed package that was installed by the package manager, or came with the OS, before installing a manually installed package with 'make' 'make install' type commands?  Just not sure if it will be installed over it or along side it.  The package manager I use is aptitude and k3b came installed with the OS.

Thanks!

Lisa

---

### Post by brian_p on 2008-06-29
> **Cubby said:**
> As a general question, should one remove a pre-installed package that was installed by the package manager, or came with the OS, before installing a manually installed package with 'make' 'make install' type commands?  Just not sure if it will be installed over it or along side it.  The package manager I use is aptitude and k3b came installed with the OS.

Install the compiled program in the /usr/local hierarchy. Both versions can then exist side-by-side.

---

