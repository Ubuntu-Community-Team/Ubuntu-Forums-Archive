---
title: "package of specific file"
date: 2005-09-10
forum: General Help
---

### Post by twelvegates on 2005-09-10
How can one deterine the package containing a specific file, say /usr/X11R6/include/X11/X.h?

---

### Post by macgyver2 on 2005-09-10
[QUOTE=twelvegates]How can one deterine the package containing a specific file, say /usr/X11R6/include/X11/X.h?[/QUOTE]
Here are two options depending on the circumstances...

If you know the file is installed on your system use
```
dpkg -S <filename>
```
If you want to search both installed *and* uninstalled packages then first install the package apt-file and then use
```
apt-file search <filename>
```
[font=Courier New][/font]

---

