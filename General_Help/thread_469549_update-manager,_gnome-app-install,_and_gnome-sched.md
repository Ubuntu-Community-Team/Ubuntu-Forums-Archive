---
title: "update-manager, gnome-app-install, and gnome-schedule will not start"
date: 2007-06-10
forum: General Help
---

### Post by DMM8787 on 2007-06-10
Similar errors come from launching each of these programs:

Traceback (most recent call last):
  File "/usr/bin/update-manager", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk

From what I can tell, this is a problem which resulted in the upgrade from python 2.4 to 2.5.1, but thats as much as I can figure out.. and that may be entirely incorrect.

I know there are work-arounds so I don't have to use these guis, but I'd still like to know why they have broken. 

Thanks in advance!

also:
I'm running feisty with python 2.5.1 and all upgraded packages from synaptic

---

### Post by Kenji Mapes on 2007-06-10
Yeah, I am having problems with my Python 2.5 packages.  If I find anything out, I will let you know.

---

