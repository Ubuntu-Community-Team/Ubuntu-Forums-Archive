---
title: "My gnome-app-installer does not load, why might this be ?"
date: 2007-08-27
forum: General Help
---

### Post by rniella on 2007-08-27
Hello all, all of a sudden my gnome-app-installer just quit working, here is a copy of the error messages if I run it from a terminal:

Thanks in advanced !!!

===========

naldo@naldo-desktop:~$ gnome-app-install 
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 30, in apport_excepthook
    import apport.report, apport.fileutils
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 17, in <module>
    import xml.dom, xml.dom.minidom
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/__init__.py", line 220, in <module>
    from xml.dom import DOMImplementation
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/DOMImplementation.py", line 1
    ELF
    ^
SyntaxError: invalid syntax

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 313, in <module>
    from AppInstall.AppInstall import AppInstall
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 80, in <module>
    from Menu import ApplicationMenu
  File "/usr/lib/python2.5/site-packages/AppInstall/Menu.py", line 14, in <module>
    import xdg.Menu
  File "/var/lib/python-support/python2.5/xdg/Menu.py", line 7, in <module>
    import locale, os, xml.dom.minidom
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/__init__.py", line 220, in <module>
    from xml.dom import DOMImplementation
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/DOMImplementation.py", line 1
    ELF
    ^
SyntaxError: invalid syntax

==================

---

### Post by aysiu on 2007-08-27
Could be a bug.
[https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/109273](https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/109273)

---

