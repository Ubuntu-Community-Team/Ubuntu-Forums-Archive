---
title: "My Fesity is going crazy.."
date: 2007-09-10
forum: General Help
---

### Post by rniella on 2007-09-10
A couple of weeks ago, after some update, I could not open the gnome-app-install program so I started playing around with Synaptic trying to solve the issue...  then I realized that I could not install other programs either.  It kept telling me that there was some errror with ubuntu-desktop and gnome-app-install not being configured correctly or broken.

Until today..  when I run the following command (as a last resource trying to bring things to normal)

sudo aptitude install -f 

 and as a result I lost now my Thunderbird !! which was my most important piece of software.. how can I bring things back to normal ??  I ran the command again sudo aptitude install -f  and got the following messages.. any clues ??  thanks !

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
E: Sub-process /usr/bin/dpkg returned an error code (1)
Un paquete no se pudo instalar. Intentado recuperarse:
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

----------------

---

