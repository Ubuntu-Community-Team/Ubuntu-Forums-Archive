---
title: "removing serpentine on ubuntu 7.1"
date: 2007-10-30
forum: General Help
---

### Post by rico16135 on 2007-10-30
ok in synaptic package manager, when I try to remove the package serpentine it also marks ubuntu-desktop for removal.  Not what I had in mind.  How can I remove this package while still keeping ubuntu-desktop?

---

### Post by dayvy on 2007-10-30
Ubuntu-desktop is a meta-package. It is a group of packages. This basically means that if you remove one part of this meta-package then by definition the meta-package must be uninstalled. This does not mean that it will uninstall any other software. Go ahead and uninstall serpentine. It'll be fine.

d.

---

### Post by vanadium on 2007-10-30
Ubuntu desktop is the "meta package". Installing that one automatically pulls in all components that belong to the "standard" Ubuntu desktop. Removing Serpentine will cause you to need to remove the Ubuntu Desktop metapackage, because it depends on among others Serpentine. It is only the tiny metapackage you are removing, though. You will not remove any other components of the Ubuntu Desktop.

I am not aware if there are negative side effects of removing the Ubuntu Desktop metapackage. If at any time, you want to "restore" the Ubuntu Desktop, then just reinstall that package.

---

