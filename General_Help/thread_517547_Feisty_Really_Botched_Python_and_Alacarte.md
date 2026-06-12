---
title: "Feisty: Really Botched Python and Alacarte"
date: 2007-08-04
forum: General Help
---

### Post by AshTR on 2007-08-04
Lemme just make this brief. For some reason Python and Alacarte are acting up on me. Looks like update-manager might be too. Not sure why. Here is what I got when trying to reinstall Python and trying to start up Alacarte.

sudo apt-get install --reinstall python
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/141kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 116238 files and directories currently installed.)
Preparing to replace python 2.5.1-0ubuntu3 (using .../python_2.5.1-0ubuntu3_all.deb) ...
Unpacking replacement python ...
Setting up python (2.5.1-0ubuntu3) ...

Setting up update-manager (0.59.23) ...
Warning: /usr/share/gconf/schemas/update-manager.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need to give at least a file to (un)register.
dpkg: error processing update-manager (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 update-manager
 update-notifier
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

alacarte
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 30, in apport_excepthook
    import apport.report, apport.fileutils
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 17, in <module>
    import xml.dom, xml.dom.minidom
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/__init__.py", line 223, in <module>
    from xml.dom.html import HTMLDOMImplementation
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/html/__init__.py", line 397, in <module>
    import codecs # Python 1.6+ only
  File "/usr/lib/python2.5/codecs.py", line 744
SyntaxError: Non-ASCII character '\x9d' in file /usr/lib/python2.5/codecs.py on line 744, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 21, in <module>
    import gettext
  File "/usr/lib/python2.5/gettext.py", line 49, in <module>
    import locale, copy, os, re, struct, sys
  File "/usr/lib/python2.5/locale.py", line 14, in <module>
    import sys, encodings, encodings.aliases
  File "/usr/lib/python2.5/encodings/__init__.py", line 31, in <module>
    import codecs, types
  File "/usr/lib/python2.5/codecs.py", line 744
SyntaxError: Non-ASCII character '\x9d' in file /usr/lib/python2.5/codecs.py on line 744, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details

---

### Post by AshTR on 2007-08-08
Please? I really need some help with this. It's been 3 days. Sorry if I'm naggy or anything, I just don't know how to fix this. I'm a bit new to Ubuntu.

EDIT: Forget it all. I'm just gonna reinstall the sucker.

---

