---
title: "save to remove this orphaned package?"
date: 2008-07-09
forum: General Help
---

### Post by Revvion on 2008-07-09
Oke so i removed some packages that forced me to remove the meta-package ubuntu-desktop, but now i have some questions about the orphaned packages i now have. Namely "gvfs-fuse" and "libglut3" is it save to remove these or is it better to keep them?

---

### Post by djbon2112 on 2008-07-09
If they come up on "sudo apt-get autoremove" then yes it's safe. If not, I'd leave them just to be sure (unless of course space is a major issue).

---

### Post by jpeddicord on 2008-07-09
I'd keep both of those, actually.

gvfs-fuse allows you to connect to remote shares and makes them accessible to other programs.
libglut3 is needed by some 3D applications.

Granted, autoremove caught them, then probably no applications depend on them. If you find that some things do not work right afterwards, I'd suggest reinstalling those (and perhaps ubuntu-desktop).

---

### Post by Revvion on 2008-07-09
oke thanks, they dont show up in autoremove but in GtkOrphan or in a custom filter with orphaned packages

---

