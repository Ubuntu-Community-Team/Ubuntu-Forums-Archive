---
title: "Latex plugin for gedit"
date: 2007-12-05
forum: General Help
---

### Post by zadig on 2007-12-05
I'm using dapper as my main machine and downloaded the latex plugin for gedit. I've put the plugin under ~/.gnome2/gedit/plugins. When I open gedit, and go to edit/preferences/plugins I see the latex plugin. The problem is I cant activate it, the check box doesnt load it. I get the following error when I open it from the terminal

Traceback (most recent call last):
  File "/home/bilgic/.gnome2/gedit/plugins/LaTeXPlugin/__init__.py", line 25, in ?
    from PluginInstance import PluginInstance
  File "/home/bilgic/.gnome2/gedit/plugins/LaTeXPlugin/PluginInstance.py", line 21, in ?
    from gedit import encoding_get_utf8, tab_get_from_document
ImportError: cannot import name encoding_get_utf8

** (gedit:21109): WARNING **: Could not load python module LaTeXPlugin


** (gedit:21109): WARNING **: Error, impossible to activate plugin 'LaTeX Plugin 0.1.2'

I have gutsy installed on another computer, and I've followed the same steps and I just works.

---

