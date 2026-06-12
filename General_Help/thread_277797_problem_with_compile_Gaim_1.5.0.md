---
title: "problem with compile Gaim 1.5.0?"
date: 2006-10-15
forum: General Help
---

### Post by MaaSTaaR on 2006-10-15
Hello ...

i am using Ubuntu 6.06 and i want compile Gaim 1.5.0 from source , but when i run "./configure" it's show these errors :

```

checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.9.6, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLib 2.0 is required to build Gaim; please make sure you have the GLib
*** development headers installed. The latest version of GLib is
*** always available at http://www.gtk.org/.

```

and i remember i tryed to compile another software (i don't remember it's name) rely on GLib and it's show for me same errors (as i remember) , so what should i do to avoid this problem ?

---

### Post by lamego on 2006-10-15
You should not be compiling applications from source unless you are an experienced user, which doesn't seem to be the case.
Please look for the applications on the synaptic package manager.

You could search and install the required library:
```
apt-cache search libglib dev
```

But you may get into other programs when using programs from the source without understanding how they are built/installed...

---

