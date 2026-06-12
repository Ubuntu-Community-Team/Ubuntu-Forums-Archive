---
title: "Add/Remove... no longer runs"
date: 2007-05-13
forum: General Help
---

### Post by Carandol on 2007-05-13
The Add/Remove... program for installing software has stopped working in my Feisty installation. The toolbar shows "Starting Add/Remove..." but then it disappears again. Synaptic is still working, so it's not the end of the world, but it's annoying. I'd reinstall it, but don't know the program name, and when I tried to run Edit Menus to find out, I discovered that's stopped working too! I haven't done anything to the system recently to change anything, other than applying updates. Any help appreciated.

---

### Post by aidanr on 2007-05-13
open a terminal and type in "gnome-app-install" and tell us if it gives back any error, and also type "alacarte"

---

### Post by Carandol on 2007-05-13
> **aidanr said:**
> open a terminal and type in "gnome-app-install" and tell us if it gives back any error, and also type "alacarte"

Yes, gnome-app-install came back with:

> Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 30, in apport_excepthook
    import apport.report, apport.fileutils
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 17, in <module>
    import xml.dom, xml.dom.minidom
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/minidom.py", line 21, in <module>
    from xml.dom.xmlbuilder import DOMImplementationLS, DocumentLS
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/xmlbuilder.py", line 214, in <module>
    class DOMEntityResolver(NewStyle):
NameError: name 'NewStyle' is not defined

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 312, in <module>
    from AppInstall.AppInstall import AppInstall
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 80, in <module>
    from Menu import ApplicationMenu
  File "/usr/lib/python2.5/site-packages/AppInstall/Menu.py", line 14, in <module>
    import xdg.Menu
  File "/var/lib/python-support/python2.5/xdg/Menu.py", line 7, in <module>
    import locale, os, xml.dom.minidom
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/minidom.py", line 21, in <module>
    from xml.dom.xmlbuilder import DOMImplementationLS, DocumentLS
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/xmlbuilder.py", line 214, in <module>
    class DOMEntityResolver(NewStyle):
NameError: name 'NewStyle' is not defined


and alacarte came back with

> Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 30, in apport_excepthook
    import apport.report, apport.fileutils
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 17, in <module>
    import xml.dom, xml.dom.minidom
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/__init__.py", line 220, in <module>
    from xml.dom import DOMImplementation
ImportError: cannot import name DOMImplementation

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 32, in <module>
    from Alacarte.MenuEditor import MenuEditor
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 19, in <module>
    import os, re, xml.dom.minidom, locale
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/__init__.py", line 242, in <module>
    from domreg import getDOMImplementation,registerDOMImplementation
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/domreg.py", line 5, in <module>
    from xml.dom.minicompat import *  # isinstance, StringTypes
ImportError: No module named minicompat


---

### Post by aidanr on 2007-05-13
yikes, the only thing i could find was [this]("https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/103001")

so try his suggestion:
sudo dpkg --configure -a

---

### Post by Carandol on 2007-05-13
> **aidanr said:**
> 
so try his suggestion:
sudo dpkg --configure -a

Nope, that makes no difference. Sadly, I'm not a programmer, so I haven't a clue what's going on. But thanks for trying! :-)

---

### Post by Carandol on 2007-05-17
Ah, problem solved! Turns out there was a glitch in the hard drive that had scrambled part of the python installation. After fixing the disk, I reinstalled the scrambled bit, and everything's working again.

---

### Post by kaskoosek on 2007-10-18
Problem is solved by reinstalling python-xml in Synaptic Package Manager.
We are unable to import DOM, which has been causing the error.

---

### Post by gazwani on 2008-01-23
Hi 

I have the same problem with the Add/Remove... program not working.

When I try to reinstall python-xml in synaptic (as suggested) I get the following error:

xml_0.8.4-8ubuntu1_amd64.deb: subprocess new pre-removal script returned error exit status 1

If I try on the command line to remove it (apt-get remove python-xml):

 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 python-xml
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help with this would be much appreciated.
Thanks

---

### Post by danceswithcats on 2008-01-23
I've got a similar problem.  The error message is

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


It comes up when I click 'apply' in add/remove or when I try to run synaptic.  When I try to run the dpkg command in terminal it says it requires superuser privileges.

It's a new install of Ubuntu Gutsy and I've been sorting out streaming preferences and so on, guided by[ this thread]("http://ubuntuforums.org/showthread.php?t=661833&highlight=starting").  I had an unsuccessful install of Googleearth and I was looking for a way to get that off my computer.

I am at the limit of my abilities.  I ran Ubuntu on my old laptop that died last week, for about a year but I am a very basic user.  Any advice would be very much appreciated.

---

### Post by danceswithcats on 2008-01-23
I feel rather silly,:oops:

I put sudo inf front of the dksg command and all was well.

Sorry to bother you

---

