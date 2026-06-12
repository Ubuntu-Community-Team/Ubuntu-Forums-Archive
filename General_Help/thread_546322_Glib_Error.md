---
title: "Glib Error"
date: 2007-09-08
forum: General Help
---

### Post by shrumhead on 2007-09-08
> checking for GLIB - version >= 2.8.0...
*** 'pkg-config --modversion glib-2.0' returned 2.14.0, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: gobject is required to build pygtk?

I went into the synaptic package manager and tried to find an older version of GLIB to uninstall but didn't see anything.  I tried running ldconfig like it suggested but that did nothing.  I'm trying to build pygtk from source to see why I might be getting pygtk errors and I think this is the why.  

Any suggestions as to what to do?

Thanks

...Shrum

---

### Post by chalex on 2007-09-08
It sounds like maybe you manually installed glib 2.14 at some point?

You can try 'apt-get install --reinstall libglib-2.0-dev' or just remove it.

---

### Post by shrumhead on 2007-09-08
Never manually installed glib 2.14 unless it was installed as a dependency as some package from and apt-get.  I used the command 'apt-get install --reinstall libglib-2.0-dev' but nothing seemed to change.  I'm still receiving the same error as I listed above.

---

### Post by Cyberyog on 2007-09-26
I'm getting the same error :confused: did you found any solution ???
Thanks.

---

