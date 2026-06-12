---
title: "strange python problem"
date: 2005-07-27
forum: General Help
---

### Post by rwabel on 2005-07-27
I've many program which don't want to start like serpentine:
```
rwabel@RALPH:~/compiling $ /usr/bin/serpentine Traceback (most recent call last):   File "/usr/bin/serpentine", line 2, in ?     import gtk, sys, gobject, gnome, os ImportError: No module named gtk 
``` 
I always need to change manually in the file python to python2.4

why is that? Is there a way to get rid of that mixup?

anyone else encounter that problem?

---

### Post by Juergen on 2005-07-27
/usr/bin/python is a symlink.

It probably points to an other/older version for which you haven't python-gtk installed.
Just re-link it.

---

### Post by rwabel on 2005-07-27
[QUOTE=Juergen]/usr/bin/python is a symlink.

It probably points to an other/older version for which you haven't python-gtk installed.
Just re-link it.[/QUOTE]
 That's strange, it points to 2.4: python -> python2.4
But still I've to change python to python2.4 in files like serpentine. It would be logical if the symlink points to python2.3 or another than 2.4 version

---

### Post by tnasniv on 2006-02-26
```
vincent@ubuntu:/usr/bin$ serpentine
Traceback (most recent call last):
  File "/usr/bin/serpentine", line 2, in ?
    import gtk
ImportError: No module named gtk
```

I changed for python2.4 at first line ..

---

