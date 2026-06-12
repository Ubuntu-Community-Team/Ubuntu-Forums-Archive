---
title: "Uninstalling Software"
date: 2008-05-22
forum: General Help
---

### Post by measekite on 2008-05-22
Windows has Add and Remove Programs for Installing and Uninstalling software.  Also many programs have an uninstall choice in the start menu.

What are the best two methods to UNINSTALL Linux programs in Ubuntu?  Are there any additional steps to remove all traces of the software including hidden files and menu items and icons?

---

### Post by drs305 on 2008-05-22
Okay, I'll start. 
1. synaptic
2. ```
sudo aptitude purge appname
```

You can read the man pages for aptitude and apt-get to see what options you have for removing via these two commands:
```

man aptitude
man apt-get
```

---

### Post by pointone on 2008-05-22
[https://help.ubuntu.com/ubuntu/desktopguide/C/add-applications.html](https://help.ubuntu.com/ubuntu/desktopguide/C/add-applications.html)

---

