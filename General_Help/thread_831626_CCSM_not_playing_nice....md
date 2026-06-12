---
title: "CCSM not playing nice..."
date: 2008-06-17
forum: General Help
---

### Post by Stealth on 2008-06-17
So, first off ccsm is not showing any icons in the menu anymore, just one of those default black image icons on every plugin. Secondly, I can't change any settings! I get an error:

  File "/usr/local/lib/python2.5/site-packages/ccm/Widgets.py", line 1398, in enable_plugin
    if conflict.Resolve ():
  File "/usr/local/lib/python2.5/site-packages/ccm/Conflicts.py", line 378, in Resolve
    conflict = KeyConflict(setting, setting.Value, ignoreOld=True)
  File "/usr/local/lib/python2.5/site-packages/ccm/Conflicts.py", line 134, in __init__
    ActionConflict.__init__(self, setting, settings, autoResolve)
  File "/usr/local/lib/python2.5/site-packages/ccm/Conflicts.py", line 94, in __init__
    if setting.Info[0] and plugin is not setting.Plugin:
IndexError: tuple index out of range

Compiz works though, just not ccsm...what do I do?

---

### Post by Stealth on 2008-06-20
Well, I was atleast able to get the settings the way I wanted by editting a Default.ini manually in .config/compizconfig or something, but I would still like ccsm to work. :P

---

### Post by Forlong on 2008-06-22
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

