---
title: "Yet another broken add/remove.. any fix at this point ?"
date: 2007-09-20
forum: General Help
---

### Post by rniella on 2007-09-20
Hello people, whats up ? somehow my add/remove got screwed up and cant install /upgrade anything, if I run sudo dpkg --configure -a  I get the message bellow, any ideas on how to fix it ??  thanks in advanced !:

naldo@naldo-desktop:~$ sudo dpkg --configure -a
Password:
Configurando gnome-app-install (0.3.31) ...
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
SyntaxError: Non-ASCII character '\xcc' in file /usr/lib/python2.5/site-packages/_xmlplus/dom/DOMImplementation.py on line 2, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details

Original exception was:
Traceback (most recent call last):
  File "/usr/sbin/update-app-install", line 18, in <module>
    from AppInstall.CoreMenu import *
  File "/usr/lib/python2.5/site-packages/AppInstall/CoreMenu.py", line 9, in <module>
    import xdg.Menu
  File "/var/lib/python-support/python2.5/xdg/Menu.py", line 7, in <module>
    import locale, os, xml.dom.minidom
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/__init__.py", line 220, in <module>
    from xml.dom import DOMImplementation
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/DOMImplementation.py", line 1
SyntaxError: Non-ASCII character '\xcc' in file /usr/lib/python2.5/site-packages/_xmlplus/dom/DOMImplementation.py on line 2, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details
dpkg: error al procesar gnome-app-install (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
Se encontraron errores al procesar:
 gnome-app-install

---

