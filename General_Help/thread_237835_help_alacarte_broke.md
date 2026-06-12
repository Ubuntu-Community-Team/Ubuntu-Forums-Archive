---
title: "help alacarte broke"
date: 2006-08-16
forum: General Help
---

### Post by Disastorm on 2006-08-16
Alacarte wont start up anymore.  I tried removing it and installing it back but at the configuring part it gives this error 

Setting up alacarte (0.8-0ubuntu12) ...
Compiling /usr/lib/python2.4/site-packages/bike/logging.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/mock.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/setpath.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/test_bikefacade.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/test_testutils.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/testall.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/testdata.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/testutils.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/cairo/__init__.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/dbus/_dbus.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
dpkg: error processing alacarte (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 alacarte

also I got some errors on the file system check at startup and ran fsck, but alacarte is still not working.

upon trying to run alacarte I get:

/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py:45: DeprecationWarning: Non-ASCII character '\xf2' in file /usr/lib/python2.4/site-packages/cairo/__init__.py on line 1, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details
  from _gtk import *
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 20, in ?
    from Alacarte.GnomeFront import GnomeFront
  File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 22, in ?
    import gtk, gtk.glade, gnome, gnome.ui, gobject
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 45, in ?    from _gtk import *
  File "/usr/lib/python2.4/site-packages/cairo/__init__.py", line 1
    m
     ^
SyntaxError: invalid syntax


nm my alacarte works again.. no idea why.  I think my RAM is currupt or something im gonna try to get new RAM.

---

