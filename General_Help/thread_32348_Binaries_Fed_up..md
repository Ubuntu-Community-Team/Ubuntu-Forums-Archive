---
title: "Binaries F***ed up."
date: 2005-05-07
forum: General Help
---

### Post by n00b1337 on 2005-05-07
every time i try to install something with dpkg, it starts downloading  .deb files for an upgrade of openoffice, claiming that i have choosen to upgrade them. However, my problem seem to be that those .debs cannot be installed, it says something like "Cannot execute binary files", neither can i remove openoffice (which i have no need of). I am very grateful for help

---

### Post by XDevHald on 2005-05-07
[QUOTE=n00b1337]every time i try to install something with dpkg, it starts downloading .deb files for an upgrade of openoffice, claiming that i have choosen to upgrade them. However, my problem seem to be that those .debs cannot be installed, it says something like "Cannot execute binary files", neither can i remove openoffice (which i have no need of). I am very grateful for help[/QUOTE]

 Do a search in your Synaptic for openoffice and lock them by selecting just **openoffice** and going to **Package > Lock Version **then try the dpkg again and see what happens from there. 

Also be sure that when you have done th dpkg, and it works be sure to go back and unlock the versions of openoffice again if you want to continue to get the new updates, but I wouldn't recomment it until you actually receive one, just to keep things clean on your end :)

---

### Post by az on 2005-05-07
Did you add foreign (non-ubuntu) repositories to your list?

Also, ubuntu-desktop depends on openoffice.  Removing open office will remove the ubuntu-desktop package.  That is okay.  It is just an empty package that exists to pull in all the dependancies.

---

