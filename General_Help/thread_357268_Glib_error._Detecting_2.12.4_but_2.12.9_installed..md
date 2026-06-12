---
title: "Glib error. Detecting 2.12.4 but 2.12.9 installed."
date: 2007-02-09
forum: General Help
---

### Post by myXtakenheart on 2007-02-09
I'm currently trying to install Captive 1.1.7, which is a program to detect and mount NTFS HDD's.
But I'm getting an error with GLIB when I go to configure it.

Heres what it spits out at me at the very end.

```
checking for GLIB - version >= 2.0.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.12.9, but GLIB (2.12.4)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: Captive requires glib-2.0 library.
```

I've installed 2.12.9 myself, and its still spitting out this error, 2.12.9 insatlled fine, but I also think that another one of my programs is thinking that its 2.12.4 also.

I'm not sure where to go from this point on.

Thanks,
-- myXtakenheart

---

