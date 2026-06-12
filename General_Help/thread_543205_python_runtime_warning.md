---
title: "python runtime warning"
date: 2007-09-04
forum: General Help
---

### Post by timmie on 2007-09-04
I get strange erorrs when running python programs from command line:

example 1: bazaar command completion
```

$: bzr st/usr/lib/python2.4/site-packages/ctypes/__init__.py:10: RuntimeWarning: Python C API version mismatch for module _ctypes: This Python has API version 1013, module _ctypes has version 1012.
  from _ctypes import Union, Structure, Array
/usr/lib/python2.4/site-packages/ctypes/__init__.py:10: RuntimeWarning: Python C API version mismatch for module _ctypes: This Python has API version 1013, module _ctypes has version 1012.
  from _ctypes import Union, Structure, Array

status   storage 

``` 

example 2 try to run Scribes (program aborts.
```

$scribes
/var/lib/python-support/python2.4/dbus/exceptions.py:8: RuntimeWarning: Python C API version mismatch for module _dbus_bindings: This Python has API version 1013, module _dbus_bindings has version 1012.
  import _dbus_bindings
/var/lib/python-support/python2.4/dbus/mainloop/glib.py:25: RuntimeWarning: Python C API version mismatch for module _dbus_glib_bindings: This Python has API version 1013, module _dbus_glib_bindings has version 1012.
  from _dbus_glib_bindings import DBusGMainLoop, gthreads_init
/var/lib/python-support/python2.4/gtk-2.0/gobject/__init__.py:30: RuntimeWarning: Python C API version mismatch for module gobject._gobject: This Python has API version 1013, module gobject._gobject has version 1012.
  from _gobject import *
```

Why do I get these errors?

Thanks!

---

