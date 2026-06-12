---
title: "Problem with pygtk and GLIB"
date: 2007-10-09
forum: General Help
---

### Post by shrumhead on 2007-10-09
Not sure what exactly it is I did or perhaps an update did to cause this problem but this is what's happening...

I try to run a program like Listen music player from the command line.  I type "listen" and get this error:

```
Traceback (most recent call last):
  File "/usr/lib/listen/listen.py", line 34, in <module>
    import pygtk
ImportError: No module named pygtk

```

So I went and downloaded the source for pygtk.  I ran ./configure and got this error: 

```
checking for GLIB - version >= 2.8.0... 
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
```

So I went to the Synaptic Package Manager and tried to reinstall python-gtk2 and python-gtk2-dev and still get the same error above (the first one, Traceback error).  So I found libglib2.0-0 in the synaptic package manager and tried to uninstall it but there were too many things it would have uninstalled with it so I just reinstalled it and libglib2.0-dev but that didn't solve the second error.  

Now I'm stuck and pretty sure the error about glib is what's holding me back but I don't know how to proceed.  Any advice?

ty

shrumhead.

---

