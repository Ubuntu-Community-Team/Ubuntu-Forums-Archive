---
title: "Trying to get SynCE"
date: 2007-03-18
forum: General Help
---

### Post by saxsux on 2007-03-18
I've spent most of the day trying to get SynCE working with my Windows Moble 5, by following the instructions on [http://www.synce.org/index.php/Syncing_via_OpenSync#SyncEngine](http://www.synce.org/index.php/Syncing_via_OpenSync#SyncEngine) (and the ones leading up to it, obviously).
I've had a bit of dependency hell, and had to compile a few things that SynCE needed that weren't in the repos, but apart from that, everything's worked fine. Until now.

I've got up to starting SyncEngine, but it wont 
Here's the output I get from running ./sync-engine/sync-engine

```

Traceback (most recent call last):
  File "./sync-engine/sync-engine", line 30, in ?
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

```

Help, anyone? :)

---

### Post by saxsux on 2007-03-19
BUMP

I'd really like to get this sorted out. 
Can anyone help?

---

