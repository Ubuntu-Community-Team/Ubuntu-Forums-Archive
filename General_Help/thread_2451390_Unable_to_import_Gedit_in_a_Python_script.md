---
title: "Unable to import Gedit in a Python script"
date: 2020-10-03
forum: General Help
---

### Post by cdelapena on 2020-10-03
I am getting the following error when running a Python script:

```
christian@christian-UX430UAR:~/.local/share/gedit/plugins$ python intelligent_text_completion.py
intelligent_text_completion.py:13: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GObject, Gedit, PeasGtk
Traceback (most recent call last):
  File "intelligent_text_completion.py", line 13, in <module>
    from gi.repository import Gtk, GObject, Gedit, PeasGtk
  File "/usr/lib/python2.7/dist-packages/gi/importer.py", line 133, in load_module
    'introspection typelib not found' % namespace)
[B]ImportError: cannot import name Gedit, introspection typelib not found

[/B]
```I tried running **sudo apt-get install gedit** and I also installed gtk2.0+ and gtk3.0+ and nothing seems to work. I did also ran **sudo apt-get install python-gi.** Interestingly, I'm able to import GObject but not Gedit:
```

christian@christian-UX430UAR:~/.local/share/gedit/plugins$ python intelligent_text_completion.py
intelligent_text_completion.py:13: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GObject, Gedit, PeasGtk
Traceback (most recent call last):
  File "intelligent_text_completion.py", line 13, in <module>
    from gi.repository import Gtk, GObject, Gedit, PeasGtk
  File "/usr/lib/python2.7/dist-packages/gi/importer.py", line 133, in load_module
    'introspection typelib not found' % namespace)
ImportError: cannot import name Gedit, introspection typelib not found
```

I have no idea what to do. Can anyone help?

---

### Post by norobro on 2020-10-03
That's a plugin for gedit not a script that you can run from the command line.

Installation instructions: [https://github.com/nymanjens/gedit-intelligent-text-completion#user-content-gedit-30-38-ubuntu-1110-or-higher](https://github.com/nymanjens/gedit-intelligent-text-completion#user-content-gedit-30-38-ubuntu-1110-or-higher)

---

