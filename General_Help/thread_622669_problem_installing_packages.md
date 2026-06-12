---
title: "problem installing packages"
date: 2007-11-25
forum: General Help
---

### Post by john91 on 2007-11-25
Recently I attempted to install a new version of flash player, and the installation froze, which subsequently kept me from installing any other new packages.  After trying to kill the installation through the terminal and then rebooting my system, the problem still persisted.  Whenever I attempt to install any other package, one of two things happens:

I get the message "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "  When I run dpkg...etc, the flash player installation begins again, and then freezes.

or

the installation of the package begins, and then switches over to installing the macromedia flash player installation that froze.  This installation then freezes, and I'm back where I started.  

Until this problem is fixed, I'm unable to install any new packages, so any help to fix this would be greatly appreciated.

---

### Post by zvacet on 2007-11-25
```
sudo dpkg --configure -a
```

---

### Post by john91 on 2007-11-25
I ran the command using sudo in the first place... and like I said, it simply began the flash player download again and then froze, leaving me back where I was in the first place.

---

