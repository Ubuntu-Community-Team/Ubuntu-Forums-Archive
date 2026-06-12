---
title: "Gnome-VFS issues causing desktop failure"
date: 2007-10-26
forum: General Help
---

### Post by Leland McInnes on 2007-10-26
I just installed Gutsy on my laptop, over an old Fedora installation, and nautilus is failing due to Gnome-VFS having issues. Specifically, on trying to run nautilus (or, indeed, anything that uses Gnome-VFS to acccess files, such as baobab) I get the following error:

libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libfile.so' (libstdc++.so.5: cannot open shared object file: No such file or directory)

(libfile.so is exactly where it should be) I've tried re-installing libgnomevfs2 in case, but to no avail. Is there something obvious I may be missing? If not I would appreciate any help in diagnosing this.

---

### Post by Leland McInnes on 2007-10-27
Problem solved: for some reason libstdc++5 was not installed, but was being called. Installing it remedied the situation.

---

