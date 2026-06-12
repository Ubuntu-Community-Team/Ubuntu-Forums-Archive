---
title: "&quot;avg75fld-r47-a1025.i386.deb&quot; cannot be installed"
date: 2007-08-20
forum: General Help
---

### Post by sdim on 2007-08-20
While trying to istall "avg75fld-r47-a1025.i386.deb",the two things attached below came up as messages.
Any ideas?

---

### Post by rbmorse on 2007-08-20
Make sure that either the directory with the avg .deb is the current directory, or use the full path to the ,deb and try:

sudo dpkg -i --force-overwrite avg75-<tab><enter>

.

---

### Post by sdim on 2007-08-21
Thank you, Rbmorse.It seems to have worked.It says that it has been installed.
Nevertheless,I can't find it to create a shortcut.Any ideas?

---

