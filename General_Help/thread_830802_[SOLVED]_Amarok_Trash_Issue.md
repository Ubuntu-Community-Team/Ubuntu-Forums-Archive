---
title: "[SOLVED] Amarok Trash Issue"
date: 2008-06-16
forum: General Help
---

### Post by Kristopher on 2008-06-16
Under Gnome and a fresh install of 8.04, Amarok is telling me the following

"could not start process Unable to create io-slave: klauncher said: unknown protocol 'trash'"

If i say just permanently delete its ok, is there a solution to this?

---

### Post by Kristopher on 2008-06-16
Solved - was missing "kdebase-kio-plugins"

---

### Post by martinschroeder on 2008-12-29
In Intrepid you have to install the package mediamanager.

Edit:
I have to correct myself. Installing mediamanager didn't solve the problem.
But now I have the "amarok automaticly unmounts all drives on close"-problem...
Maybe the amarok developers should care more about gnome users...

---

### Post by martinschroeder on 2009-01-16
The only thing I can do is removing the files permanently without moving to trash.
That is annoying because on FAT-Drives, the files may be named equally upper- or lowercase and because of this the same file is displayed twice sometimes. When i delete one "version" of it, the one real existing file is deleted and hard to restore...

---

