---
title: "gnome-app-install (add/remove) Not Loading"
date: 2008-01-18
forum: General Help
---

### Post by LavianoTS386 on 2008-01-18
I couldn't find the answer to this specific problem.

This is what I get when I try to use the terminal to load gnome-app-install...

> Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 27, in <module>
    from AppInstall.activation import main
  File "/usr/lib/python2.5/site-packages/AppInstall/activation.py", line 22, in <module>
    import gconf
ImportError: No module named gconf



Any idea what's going on? I've tried uninstalling gnome-app-install, and then reinstalling it but I'm having no luck.

---

### Post by gvartser on 2008-01-18
Have you tried to install gconf?

#) [COLOR="DarkGreen"]sudo apt-get install gconf2 python-gconf[/COLOR]

Best regz,
/G

---

