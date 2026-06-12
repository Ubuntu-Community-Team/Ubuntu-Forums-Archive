---
title: "synaptic wants to remove vital system packages when i try to install others"
date: 2006-11-18
forum: General Help
---

### Post by Atmospherian on 2006-11-18
On Edgy 6.10, when i try to install the libgl1-mesa-dev or libglu1-mesa-dev packages, synaptic wants to remove the following packages: 

libgl1-mesa-dri
libgl1-mesa-glx
ubuntu-desktop
xorg

the first two i am not really concerned about, but the second two are vital to the system, seems very odd that those would need to be removed in order to install some development libraries. 

Anything i can do to manually install these packages or remove the need to uninstall those important system packages?

Thanks in advance.

~Atmospherian

---

### Post by janbockaert on 2006-11-18
as far as i know, ubuntu desktop is not a vital system package, it is, i believe, a metapackage, that is used to install all the packages of ubuntu-desktop with one sigle click. if you remove one of the packages this meta-package has installed, this metapackage also gets removed. Xorg also is a meta package.
 so i guess, xorg gets removed because libgl1-mesa-glx gets removed, and ubuntu-desktop gets removed because xorg gets removed.

However, i can not tell you it is safe to remove the libgl1 packages, that i do not know.

---

### Post by Atmospherian on 2006-11-18
apparently i had some repository issues with synaptic. under settings they were all turned off, which was giving me errors about packages that were requried but that weren't going to be installed. once i fixed the reops, those errors disappeared and i was able to install the packages.

---

