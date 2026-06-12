---
title: "gWakeOnLan 0.6.2 - &quot;PyGIWarning: Gtk was imported without specifying a version first&quot;"
date: 2016-06-10
forum: General Help
---

### Post by felgro on 2016-06-10
Hi,

I need a wake on lan app for local use. I tried to install gWakeOnLan from the AppGrid center but a) install failed silently and b) it is an ancient version anyway. So I purged it and installed the current version from source as per instructions at -

[http://www.muflone.com/gwakeonlan/english/index.html](http://www.muflone.com/gwakeonlan/english/index.html)

It appeared to install correctly with no errors. However when I attempt to start it, I get the following error dump which is like Chinese to me and google doesn't have any obvious pointers -

```
:~$ gwakeonlan 
/usr/local/lib/python2.7/dist-packages/gwakeonlan/functions.py:24: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/dist-packages/gwakeonlan/app.py", line 35, in startup
    self.ui = MainWindow(self, self.settings)
  File "/usr/local/lib/python2.7/dist-packages/gwakeonlan/ui.py", line 34, in __init__
    self.loadUI()
  File "/usr/local/lib/python2.7/dist-packages/gwakeonlan/ui.py", line 58, in loadUI
    builder.add_from_file(FILE_UI_MAIN)
GLib.Error: g-file-error-quark: Failed to open file '/usr/share/gwakeonlan/ui/main.glade': No such file or directory (4)
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/dist-packages/gwakeonlan/app.py", line 52, in activate
    self.ui.run()
AttributeError: 'Application' object has no attribute 'ui'
```

Can someone enlighten me what this means? I am python ignorant. Or failing that, can anyone suggest an alternate WoL tool - preferably with GUI, though without will suffice. The ones available in the various software centers are all woefully out of date and have defunct author websites.

---

### Post by pqwoerituytrueiwoq on 2016-06-10
Do you really need a GUI for WOL?
[etherwake]("apt:etherwake") and [wakeonlan]("apt:wakeonlan") both work just fine

your GUI was made for a older version of the gui and needs a update

---

### Post by felgro on 2016-06-10
> **pqwoerituytrueiwoq said:**
> Do you really need a GUI for WOL?
[etherwake]("apt:etherwake") and [wakeonlan]("apt:wakeonlan") both work just fine

your GUI was made for a older version of the gui and needs a update

I didn't try wakeonlan as owners site is 404. OK, I'll try it.

---

