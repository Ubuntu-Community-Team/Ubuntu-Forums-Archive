---
title: "Can't install OpenOffice updates due to prelink"
date: 2005-05-01
forum: General Help
---

### Post by NeoChaosX on 2005-05-01
Okay, been trying to install the latest updates for OpenOffice, but when it gets to certain packages, the install screws up

```
Undoing prelinking of OpenOffice.org binaries... run-parts: /usr/share/openoffice.org-debian-files/hooks/postinst.d/prelink exited with return code 1
dpkg: error processing openoffice.org-bin (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openoffice.org-gtk-gnome:
 openoffice.org-gtk-gnome depends on openoffice.org-bin (>= 1.1.2+1.1.3); however:
  Package openoffice.org-bin is not configured yet.
dpkg: error processing openoffice.org-gtk-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on openoffice.org-gtk-gnome; however:
  Package openoffice.org-gtk-gnome is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-bin
 openoffice.org-gtk-gnome
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've tried removing and reinstalling openoffice, but the same error keeps coming up when I reinstall it, and I don't know what to do. SI've tried disabling prelink, but the error still keeps coming up. What do I do now?

EDIT: Nevermind, removing prelink automatically fixed the problem.

---

### Post by jaegen on 2005-05-04
Thank you very much for updating with your solution (and for finding the solution in the first place).  I think this has plagued a few of us ([http://www.ubuntuforums.org/showthread.php?t=30309](http://www.ubuntuforums.org/showthread.php?t=30309)).

Jaegen

---

