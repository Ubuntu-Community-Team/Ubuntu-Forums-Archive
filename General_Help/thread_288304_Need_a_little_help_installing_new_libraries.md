---
title: "Need a little help installing new libraries"
date: 2006-10-29
forum: General Help
---

### Post by techweenie on 2006-10-29
I am in the process of installing gnash so I can view flash on my 64 bit system, but it is turning out to be quite an adventure.  The dependencies list is a mile-and-a-half long, so I started going through them one by one and updating/installing as necessary.  Most of them were available through synaptic, but the ones that weren't I'm installing from source files.  I'm currently trying to gtk+ installed, but I get the following error:

```
checking for GLIB - version >= 2.12.0...
*** 'pkg-config --modversion glib-2.0' returned 2.12.4, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.12.0 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/pub/gtk/.
```

After doing some snooping around, it appears the older version of glib-2.0 is in /usr/lib, but the new version is in /usr/local/lib.  Should I have used './configure --prefix=/usr/lib' when installing glib?  Or is there something else I can do to get the link pointing to the new version?  I'm somewhat of a n00b, so if I need to edit files or modify paths or anything like that then please fully explain how to do so.

---

