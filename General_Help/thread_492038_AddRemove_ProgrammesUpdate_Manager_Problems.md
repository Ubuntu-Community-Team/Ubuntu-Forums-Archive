---
title: "Add/Remove Programmes/Update Manager Problems"
date: 2007-07-04
forum: General Help
---

### Post by helliewm on 2007-07-04
Neither Add/Remove Programmes nor Update Manager will install any programmes. Sudo apt-get does work.

sudo gnome-app-install gives this error message.


helen@helen-laptop:~$ sudo gnome-app-install
warning: could not initiate dbus

** (gnome-app-install:6108): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1532: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)


Anyone ideas about this?

Helen

---

### Post by rodo-&gt;dave on 2007-07-04
You probably already tried this, but I found this:
[http://ubuntuforums.org/showthread.php?t=317136](http://ubuntuforums.org/showthread.php?t=317136)

---

### Post by helliewm on 2007-07-04
Yes I had found that. But I tried a further suggestion 

sudo apt-get -f install

The problem is now solved. At least we now have a very simple thread for people with this issue:p:p

Helen

---

