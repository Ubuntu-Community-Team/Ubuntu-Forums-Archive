---
title: "undefined symbol: xmlPathToURI"
date: 2007-08-22
forum: General Help
---

### Post by jeffbarish on 2007-08-22
When I try to run update-manager, I get the following traceback:

Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in ?
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 59, in ?
    import dbus
  File "/var/lib/python-support/python2.4/dbus/__init__.py", line 1, in ?
    from _dbus import *
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 48, in ?
    from proxies import *
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 2, in ?
    import introspect_parser
  File "/var/lib/python-support/python2.4/dbus/introspect_parser.py", line 1, in ?
    import libxml2
  File "/usr/local/lib/python2.4/site-packages/libxml2.py", line 1, in ?
    import libxml2mod
ImportError: /usr/local/lib/python2.4/site-packages/libxml2mod.so: undefined symbol: xmlPathToURI


I tried reinstalling everything related to libxml2 (libxml2, libxml2-utils, python-libxml2, libcroco3, docbook-xml).  Same error.  There's another thread that reported the same problem(Trying to get SynCE), but there is no resolution posted.  Anyone have any ideas?

---

