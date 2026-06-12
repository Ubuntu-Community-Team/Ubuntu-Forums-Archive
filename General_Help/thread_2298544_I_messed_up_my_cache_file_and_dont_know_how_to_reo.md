---
title: "I messed up my cache file and dont know how to reopen it."
date: 2015-10-12
forum: General Help
---

### Post by brennan3 on 2015-10-12
E: Syntax error /etc/apt/apt.conf.d/70debconf:3: Extra junk after value
this is all it says for most commands.

---

### Post by deadflowr on 2015-10-12
Here, compare what your file says with this
```
// Pre-configure all packages with debconf before they are installed.
// If you don't like it, comment it out.
DPkg::Pre-Install-Pkgs {"/usr/sbin/dpkg-preconfigure --apt || true";};
```
this is the default for that file.


also, it's not a cache file, by the way.

---

### Post by Geoffrey_Arndt on 2015-10-12
You can use sudo gedit followed by the full path and file name you want to edit.   Copy & paste the file example text provided in post above.  Save the changes and you should be done.

---

### Post by brennan3 on 2015-10-13
Thanks!

---

