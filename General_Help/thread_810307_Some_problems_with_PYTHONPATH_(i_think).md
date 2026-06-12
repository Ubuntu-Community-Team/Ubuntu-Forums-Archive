---
title: "Some problems with PYTHONPATH (i think)"
date: 2008-05-28
forum: General Help
---

### Post by Valad on 2008-05-28
Hy guys!

Not so far, i'm consider that i can't run update-manager and some other programs (like Frets On Fire game).

For example:
```

Traceback (most recent call last):
  File "/usr/bin/update-manager", line 25, in <module>
    import pygtk
ImportError: No module named pygtk

```
But python-gtk and other stuff is installed. And my laptop with similar software configuration works well. Any thoughts?
I'm use Ubuntu 8.04 (Hardy Heron).

Thanks for help!

---

### Post by pointone on 2008-05-28
Run "python" from the command line and enter the following commands:

```
import sys
sys.path
import pygtk
```

Post the output here.

---

### Post by Valad on 2008-05-28
```
>>> import sys
>>> sys.path
['', '/usr/lib/python25.zip', '/usr/lib/python2.5', '/usr/lib/python2.5/plat-linux2', '/usr/lib/python2.5/lib-tk', '/usr/lib/python2.5/lib-dynload', '/usr/local/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages']
>>> import pygtk
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named pygtk
>>> 

```

P.S. Modules like OpenGL, cairo, etc also doesn't import(

---

### Post by pointone on 2008-05-29
On my installation, I have a significant number more locations in my Python path. Specifically, "/var/lib/python-support/python2.5", where pygtk.py resides. 

I believe this is added to the path by "/usr/sbin/update-python-modules", but I am not sure why it wouldn't be running on your system. If you run it yourself, does this solve the problem?

Alternatively, you could manually add to your Python path using:

```
export PYTHONPATH=/var/lib/python-support/python2.5
```

...but something is really wrong here.

Perhaps reinstalling python-support would help:

```
sudo apt-get install python-support --reinstall
```

---

### Post by Valad on 2008-05-29
Thanks for advice, but nothing, except setting PYTHONPATH directly doesn't work for me. I'll try to use my laptop's PYTHONPATH on my desktop - maybe this helps.

---

### Post by Valad on 2008-05-29
Heh, nothing helps. I'll backup my files and reinstall Ubuntu. That's not right, but i want to work, not to spend few weeks to find solution:) However , thanks a lot for the help!

---

### Post by s010101 on 2008-11-26
Im having the same problem problem on ubuntu 8.10.
suggested solutions does not help, unfortunately, and i really don't feel like reinstalling ubuntu for such a problem.
can anybody come with a suggestion for a solution.

any help is appreciated !

---

### Post by fabio78 on 2009-05-26
i'm having the same problem to, little bit different
-fresh install of hardy
- pygtk does import without warning but GDK does not , like:

 window = gtk.GtkWindow(gtk.WINDOW_TOPLEVEL)
AttributeError: 'module' object has no attribute 'GtkWindow'

with 9.04 everything just works...

---

