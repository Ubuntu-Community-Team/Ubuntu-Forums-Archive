---
title: "Programs seeming to break?"
date: 2005-04-27
forum: General Help
---

### Post by Justin Shreve on 2005-04-27
I havn't used a binary system in awhile, but it seems like everything I am installing breaks...

First, after installing bluefish, it doesn't want to load and comes up with the error:

bluefish: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.3.4' not found (required by bluefish)


Though GLIB is installed.

Also when running a program called gparted:

gparted
gparted: Symbol `_ZTIN4Glib9InterfaceE' has different size in shared object, consider re-linking
gparted: Symbol `_ZTIN4Glib10ObjectBaseE' has different size in shared object, consider re-linking
gparted: Symbol `_ZTIN4Glib6ObjectE' has different size in shared object, consider re-linking
gparted: Symbol `_ZTIN3Gtk6WidgetE' has different size in shared object, consider re-linking
Segmentation fault

Shows, the first is installed with apt-get, and the second with alien.

---

