---
title: "Compiling problem"
date: 2006-09-10
forum: General Help
---

### Post by Poundex on 2006-09-10
I'm trying to compile PHP-GTK2 Under Ubuntu but every time I try I get this:
```
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.6.0...
*** 'pkg-config --modversion glib-2.0' returned 2.6.6, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: PHP-GTK 2.x requires GLib 2.6.0 or higher
```

I looked, and I don't have an /etc/ld.so.conf, just an /etc/ld.so.cache and LD_LIBRARY_PATH Isn't set.

Could anyone please shed some light on the matter?

Thanks.

---

