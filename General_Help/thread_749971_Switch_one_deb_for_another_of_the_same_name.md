---
title: "Switch one deb for another of the same name?"
date: 2008-04-09
forum: General Help
---

### Post by TheForkOfJustice on 2008-04-09
I wish to remove one version of a deb and exchange it for one of my own making but I don't know how to do that without removing a mess of dependencies and having to reinstall.them again (which could undo much of the work I've already done)..

Is there a way to do this in one single command?

---

### Post by ryanhaigh on 2008-04-09
```
sudo dpkg -i yourpackage.deb
``` should take care of that unless the version you have created is not compatible with the applications it is dependant on.

---

