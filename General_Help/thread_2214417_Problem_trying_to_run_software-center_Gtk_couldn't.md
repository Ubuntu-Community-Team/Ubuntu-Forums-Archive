---
title: "Problem trying to run software-center: Gtk couldn't be initialized"
date: 2014-04-01
forum: General Help
---

### Post by tirengarfio2 on 2014-04-01
Hi, 

Im getting this error when trying to run sofware center:

```
Traceback (most recent call last):
  File "/usr/bin/software-center", line 25, in <module>[/HTML]    from gi.repository import Gtk, GObject
  File "/usr/lib/python2.7/dist-packages/gi/importer.py", line 76, in load_module
    dynamic_module._load()
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 224, in _load
    overrides_modules = __import__('gi.overrides', fromlist=[self._namespace])
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gtk.py", line 1533, in <module>
    raise RuntimeError("Gtk couldn't be initialized")
RuntimeError: Gtk couldn't be initialized
```

Im on Gnome Shell and Ubuntu 13.10

---

### Post by ibjsb4 on 2014-04-01
Try a different package manager, I assume synaptic will run in gnome-shell.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

```
sudo apt-get install synaptic
```

---

