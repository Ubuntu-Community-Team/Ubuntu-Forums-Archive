---
title: "Access Rights"
date: 2007-05-22
forum: General Help
---

### Post by MrMadison on 2007-05-22
When I try to edit my sources.list
It says I don't have the permission to edit it or its parent folder.
Anyone know how I can fix this?
Thanks in advance 
-Madison

---

### Post by newlinux on 2007-05-22
use sudo


[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by MrMadison on 2007-05-22
Yes, I've tried that. But I'm trying to physically drag and drop a new sources.list into the /etc/apt/ folder.

---

### Post by reclusivemonkey on 2007-05-22
Using

```

gksudo -S nautilus

```

Should give you a root file browser; just do all your "drag and drop" in that Window, don't try and drag and drop from a normail user window to that one.

---

### Post by vanadium on 2007-05-22
You can run a nautilus with root rights using 

gksudo nautilus

However, your safer bet will be 1) to create a backup copy of your sources.list and 2) to open your sources.list in gedit with root rights:

gksudo gedit /etc/apt/sources.list

Open your new file on a new tab, copy paste all the new content into the sources.list, then save.

Be carefull with sudo or gksudo, because you can quickly damage your system.

---

