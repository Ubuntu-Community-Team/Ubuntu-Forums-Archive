---
title: "[SOLVED] Can't Empty Trash"
date: 2008-06-11
forum: General Help
---

### Post by ezekiel000 on 2008-06-11
I've got 2 files in the Trash that were deleted off the home partition that stay when I empty the trash, I've looked for the /home/.Trash folder but it seems to have disappeared in it's place is a new link /home/.directory that links to /etc/kubuntu-default-settings/directory-home which is strange as I haven't got anything to do with Kubuntu, KDE or QT installed. 

I can still delete off all other partitions and the .Trash folders are still there. I tried looking around as root and still found nothing (My usual way of killing off files that just won't go).

Anyone have any ideas of how to fix this?

I'm running:
Ubuntu 8.04 (Fully updated)
Gnome 2.22.2
Deleted Items Applet 2.22.2
Nautilus 2.22.3

---

### Post by sisco311 on 2008-06-11
In hardy the trash is in ~/.local/share/Trash/files/

Open the file browser as root to delete the files.

---

### Post by ezekiel000 on 2008-06-11
Thanks that did the trick.

---

