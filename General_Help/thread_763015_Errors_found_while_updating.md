---
title: "Errors found while updating"
date: 2008-04-22
forum: General Help
---

### Post by pfwd.tech on 2008-04-22
Hi, When I run an update using:
```
sudo apt-get update 
```I get this error:
```
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-common
 openoffice.org-style-human
 python-uno
 openoffice.org-writer
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
 openoffice.org-filter-mobiledev
 openoffice.org-gtk
 openoffice.org-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Is there any way I can sort this?

---

### Post by blazemore on 2009-02-02
What happens if you run ```
sudo apt-get install -f
```

---

### Post by pfwd.tech on 2009-02-05
Thanks that sorted the problem

---

