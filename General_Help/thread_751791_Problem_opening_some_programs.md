---
title: "Problem opening some programs"
date: 2008-04-10
forum: General Help
---

### Post by GTengineer on 2008-04-10
Hi all,

Bare with me I am a noob. I was messing around trying to fix screenlets because it was not running with an error saying it could not import pygtk. Anyway, I followed some advise that I found so I compiled and installed: pycairo, pygobject, and pygtk. But now some of my Ubuntu programs under the Prefences menu will not start. I am also having the same problem when trying to open sbackup which is failing to open with this error message:

> $ gksu simple-backup-config
  File "/usr/sbin/simple-backup-config", line 28, in <module>
    import gtk
  File "/usr/local/lib/python2.5/site-packages/gtk-2.0/gtk/__init__.py", line 38, in <module>
    import gobject as _gobject
  File "/usr/local/lib/python2.5/site-packages/gtk-2.0/gobject/__init__.py", line 30, in <module>
    from gobject.constants import *
  File "/usr/local/lib/python2.5/site-packages/gtk-2.0/gobject/constants.py", line 22, in <module>
    from _gobject import type_from_name
ImportError: /usr/local/lib/python2.5/site-packages/gtk-2.0/gobject/_gobject.so: undefined symbol: PyUnicodeUCS2_FromObject

I do not care about screenlets anymore, I just want to restore my desktop. Can anyone help me?
Thanks

---

### Post by GTengineer on 2008-04-10
Update:

When I try to load the restore utility of sbackup it gives me this error:

> $ sudo simple-restore-gnome 
Failed to load Python GTK/Gnome bindings. Please check your Gnome installation.


Update 2:

I have found that the problem is associated with python and some missing modules

> $ sudo python ../share/sbackup/simple-backup-config.py
Traceback (most recent call last):
  File "../share/sbackup/simple-backup-config.py", line 28, in <module>
    import gtk
ImportError: No module named gtk

and

> $ sudo python ../share/sbackup/simple-restore-gnome.py 
Traceback (most recent call last):
  File "../share/sbackup/simple-restore-gnome.py", line 30, in <module>
    import srestore
  File "/usr/share/sbackup/srestore.py", line 29, in <module>
    import gnome.vfs as gnomevfs
ImportError: No module named gnome.vfs

---

### Post by GTengineer on 2008-04-11
Bump

I tried installing kde thinking it was gnome related but I get the same issue in kde, which leads me to believe it is not desktop related and something to do with python.

---

### Post by 3rdalbum on 2008-04-11
What happens if you try reinstalling the affected packages:

```
sudo apt-get install --reinstall python-cairo python-cairo-dev python-gtk2 python-gtk2-dev python-gtkhtml2
```

That will reinstall the repository versions. I had a similar problem a little while ago with a version of libfreetype that I had compiled, and reinstalling the repo version fixed it.

---

### Post by GTengineer on 2008-04-11
> **3rdalbum said:**
> What happens if you try reinstalling the affected packages:

```
sudo apt-get install --reinstall python-cairo python-cairo-dev python-gtk2 python-gtk2-dev python-gtkhtml2
```

That will reinstall the repository versions. I had a similar problem a little while ago with a version of libfreetype that I had compiled, and reinstalling the repo version fixed it.

Hi 3rdalbum many thanks for the suggestion. I tried it but it did not fix the problem. I am still getting the same error messages from my second post. Other programs like acrobat reader, and some in the Preference menu will not open either. This is very frustrating because this is my work OS and I cannot afford much down time. Which reminds me (Note to self: don't screwup with Ubuntu anymore)

---

