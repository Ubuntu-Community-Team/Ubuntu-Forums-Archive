---
title: "Having a problem with pygtk"
date: 2007-09-07
forum: General Help
---

### Post by shrumhead on 2007-09-07
I'm getting this error 

```
Traceback (most recent call last):
  File "/usr/lib/listen/listen.py", line 34, in <module>
    import pygtk
ImportError: No module named pygtk

```

I was recently trying to get gdesklets to work and was getting an error about python.h so I installed python from source and now I am getting the error listed above.  I assume installing from source installed the files in different paths than if I were to have done it from the synaptic package manager so how can I go about fixing this?  I have tried reinstalling pygtk2 from from the synaptic package manager by marking it for reinstall.  I didn't want to remove it completely because it listed a lot of other packages that looked important to keeping the desktop running.

---

### Post by shrumhead on 2007-09-08
bump, still having trouble, any suggestions?

---

### Post by shrumhead on 2007-09-08
Gonna go ahead and uninstall pygtk 2 and reinstall and hope it doesn't mess up anything too important.  Anyone have any ideas before I do?

EDIT:: Not gonna uninstall it afterall.  The synaptic package manager wanted to remove too many other important packages.

---

### Post by shrumhead on 2007-09-08
Just tried to build pygtk from source and got this error, I assume it is why pygtk is not installing properly.  How should I proceed?

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


---

### Post by shrumhead on 2007-09-20
Still having this problem.  How would I go about uninstalling the older version of glib?

---

### Post by Maestro23 on 2007-09-20
Search for it in Synaptic (GUI).

I believe it's **libglib** you're looking for.

---

### Post by shrumhead on 2007-09-20
I reinstalled libglib 2.0 (2.12.11) in the package manager and then reinstalled python and then attempted to configure pygtk (building from source) and got the same error about glib listed above.  In the synaptic package manager there are 2 glib versions (1.2 and 2.0)  but only version 2 is installed. 

This is the error above "'pkg-config --modversion glib-2.0' returned 2.14.0, but GLIB (2.12.11)
*** was found!"  

So looking at that I figured I would just uninstall glib 2.12.11 from the synaptic package manager but when I marked it for removal it tried to take half the programs installed with it.  

How should I proceed.  I am completely lost

---

### Post by shrumhead on 2007-09-20
Well... how would I go about removing the old glib without having to use the synaptic package manager?  It wants to uninstall too many other things.

---

### Post by analogx on 2007-09-21
PLease guys someone...
Even i'm having the same problem while installing GTK :(:confused:

---

