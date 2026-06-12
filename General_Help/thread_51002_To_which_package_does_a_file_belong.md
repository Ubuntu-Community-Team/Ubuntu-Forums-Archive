---
title: "To which package does a file belong?"
date: 2005-07-22
forum: General Help
---

### Post by Manuchau on 2005-07-22
Hello,

I have the name of a file and now I would like to know to which package this file belongs. Is there a way to determine this with a command?

For example I have the file /usr/lib/libgd.so.1. Does this file belong to libgd-dev or libgd-gif1 or another package?

Thanx very much for any help.

---

### Post by Lunde on 2005-07-22
if you open Synaptics, right click on a package and choose properties, you have a section named "Installed files" where all the files from that package is listed.

There may be an easier way, but this may get you started.

---

### Post by az on 2005-07-22
packages.ubuntu.com  Scroll to the bottom and you can search packages by a file name.

---

### Post by doclivingston on 2005-07-22
If the package is installed "dpkg -S /path/to/file" will work from a terminal.

---

### Post by cutOff on 2005-07-22
[QUOTE=doclivingston]If the package is installed "dpkg -S /path/to/file" will work from a terminal.[/QUOTE]
Still better

$ dpkg -L package

---

