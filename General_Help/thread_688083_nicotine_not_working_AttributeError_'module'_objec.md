---
title: "nicotine not working: AttributeError: 'module' object has no attribute ."
date: 2008-02-05
forum: General Help
---

### Post by aeymxq on 2008-02-05
nicotine doesn't work, and when i run it in the terminal i get this error: 

Traceback (most recent call last):
  File "/usr/bin/nicotine", line 154, in <module>
    from pynicotine.gtkgui import frame
  File "/var/lib/python-support/python2.5/pynicotine/gtkgui/frame.py", line 7, in <module>
    from pynicotine.pynicotine import NetworkEventProcessor
  File "/var/lib/python-support/python2.5/pynicotine/pynicotine.py", line 14, in <module>
    import transfers
  File "/var/lib/python-support/python2.5/pynicotine/transfers.py", line 23, in <module>
    from gtkgui.utils import recode2
  File "/var/lib/python-support/python2.5/pynicotine/gtkgui/utils.py", line 262, in <module>
    class ImageLabel(gtk.HBox):
AttributeError: 'module' object has no attribute 'HBox'

please help!

---

### Post by Toet on 2008-02-05
Did you try a reinstall?

---

### Post by aeymxq on 2008-02-05
uh, yeah.

---

