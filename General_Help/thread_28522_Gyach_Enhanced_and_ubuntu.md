---
title: "Gyach Enhanced and ubuntu"
date: 2005-04-20
forum: General Help
---

### Post by Dragon546 on 2005-04-20
Hi I used alien to convert the rpm to deb packages installed all fine but I am getting errors when I start pyvoice heres what the terminal messages say I am using Ubuntu 5.04 and latest pyvoice

/usr/local/share/gyach/pyvoice/pytsp.py:2: RuntimeWarning: Python C API version mismatch for module pytspc: This Python has API version 1012, module pytspc has version 1011.
import pytspc
/usr/local/share/gyach/pyvoice/pyvoiceui.py:161: DeprecationWarning: use gtk.UIManager
itemf=ItemFactory(MenuBar, "<main>", ag)
/usr/local/share/gyach/pyvoice/pyvoiceui.py:264: DeprecationWarning: use gtk.TreeView
self.nmlist=CList(3,[' I ',' '+_('Name')+' ',' '+_('Alias')+' '])
/usr/local/share/gyach/pyvoice/pyvoiceui.py:298: Warning: unsupported arithmetic operation for flags type
prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
Traceback (most recent call last):
File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1027, in ?
runApp()
File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1015, in runApp
pyvoicegui()
File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 298, in __init__
prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
TypeError: flag values must be strings, ints or tuples
Segmentation fault

What dependencies am I missing ????

---

### Post by sabitha on 2005-09-28
why u dont try this :
[http://ubuntuforums.org/showthread.php?t=69840&highlight=gyach+enhanced](http://ubuntuforums.org/showthread.php?t=69840&highlight=gyach+enhanced)

---

