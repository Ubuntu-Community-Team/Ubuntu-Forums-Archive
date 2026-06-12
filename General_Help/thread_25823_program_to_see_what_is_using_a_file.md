---
title: "program to see what is using a file?"
date: 2005-04-11
forum: General Help
---

### Post by Reb on 2005-04-11
I need to figure out what is using /dev/hda (and not allowing it to unmount) but I can't remember the command for this. Anybody know?

---

### Post by reid on 2005-04-11
[QUOTE=Reb]I need to figure out what is using /dev/hda (and not allowing it to unmount) but I can't remember the command for this. Anybody know?[/QUOTE]
fuser -m *filename*
do man fuser to see the other options.  This is a very useful program.

Good luck!

Reid

---

### Post by Reb on 2005-04-11
Damn gam_server... something needed for famd (which afaik KDE doesn't use).

---

