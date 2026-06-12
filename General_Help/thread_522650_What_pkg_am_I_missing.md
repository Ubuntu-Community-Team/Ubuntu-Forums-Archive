---
title: "What pkg am I missing?"
date: 2007-08-10
forum: General Help
---

### Post by TeaSwigger on 2007-08-10
Hello :) Just installed XAMPP For Linux, and it's up and running; the trouble is that their control panel won't open. So I tried to open it via Konsole and this is the full result:

```
Traceback (most recent call last):
  File "/opt/lampp/share/xampp-control-panel/xampp-control-panel.py", line 21, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 43, in <module>
    "PyGTK requires PyGObject 2.11.1 or higher, but %s was found" % (ver,))
ImportError: PyGTK requires PyGObject 2.11.1 or higher, but () was found

```

Can anyone tell from this what may be missing?

---

### Post by yabbadabbadont on 2007-08-10
Probably python-gtk2

Edit: Never mind.  Just read the error again and python-gtk2 is likely already installed.

---

### Post by yabbadabbadont on 2007-08-10
Actually, upon reading it yet again, do you have python-gobject installed?

---

### Post by ross9885 on 2007-08-10
Looks like you need the package python-gobject and maybe python-gobject-dev too.

---

### Post by TeaSwigger on 2007-08-10
> **yabbadabbadont said:**
> Actually, upon reading it yet again, do you have python-gobject installed?

Thanks folks. Alas both Python-gobject and python-gobject-dev are already installed, so it's not that.

EDIT: python-gtk2 and python-gtk2-dev are also already installed.

---

### Post by TeaSwigger on 2007-08-13
Anyone else care to take another shot at this?

To the above I can add from olive gtk:

```

  File "/usr/bin/olive-gtk", line 52, in <module>
    print >>sys.stderr, _('You need to install python-glade2 and/or pygtk2 (gtk2) or set your PYTHONPATH correctly.\ntry: export PYTHONPATH=/usr/local/lib/python2.4/site-packages/')
NameError: name '_' is not defined

```

python-glade2 and pygtk2 (gtk2) are installed.

---

