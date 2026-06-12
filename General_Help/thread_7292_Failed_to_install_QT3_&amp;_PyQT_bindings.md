---
title: "Failed to install QT3 &amp; PyQT bindings"
date: 2004-12-05
forum: General Help
---

### Post by stodge on 2004-12-05
I tried to install the QT3 libraries and applications and PyQT, the Python bindings to same libary. The installation failed for some reason:

> 
Preconfiguring packages ...
Selecting previously deselected package libqscintilla3.
(Reading database ... 101719 files and directories currently installed.)
Unpacking libqscintilla3 (from .../libqscintilla3_1.2-6_i386.deb) ...
Selecting previously deselected package python2.3-sip-qt3.
Unpacking python2.3-sip-qt3 (from .../python2.3-sip-qt3_3.10.1-2ubuntu1_i386.deb) ...
Selecting previously deselected package python2.3-qt3.
Unpacking python2.3-qt3 (from .../python2.3-qt3_3.11-4_i386.deb) ...
Selecting previously deselected package python2.3-qt3-gl.
Unpacking python2.3-qt3-gl (from .../python2.3-qt3-gl_3.11-4_i386.deb) ...
Selecting previously deselected package python2.3-qtext.
Unpacking python2.3-qtext (from .../python2.3-qtext_3.11-4_i386.deb) ...
Setting up libqscintilla3 (1.2-6) ...

Setting up python2.3-sip-qt3 (3.10.1-2ubuntu1) ...
  File "/usr/lib/python2.3/site-packages/_spe/plugins/pychecker2/tests/badparse.py", line 1
    ===
     ^
SyntaxError: invalid syntax

dpkg: error processing python2.3-sip-qt3 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.3-qt3:
 python2.3-qt3 depends on python2.3-sip-qt3 (>= 3.10); however:
  Package python2.3-sip-qt3 is not configured yet.
 python2.3-qt3 depends on python2.3-sip-qt3 (<< 4.0); however:
  Package python2.3-sip-qt3 is not configured yet.
dpkg: error processing python2.3-qt3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.3-qt3-gl:
 python2.3-qt3-gl depends on python2.3-sip-qt3 (>= 3.10); however:
  Package python2.3-sip-qt3 is not configured yet.
 python2.3-qt3-gl depends on python2.3-sip-qt3 (<< 4.0); however:
  Package python2.3-sip-qt3 is not configured yet.
 python2.3-qt3-gl depends on python2.3-qt3 (>= 3.11-4); however:
  Package python2.3-qt3 is not configured yet.
dpkg: error processing python2.3-qt3-gl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.3-qtext:
 python2.3-qtext depends on python2.3-qt3 (= 3.11-4); however:
  Package python2.3-qt3 is not configured yet.
dpkg: error processing python2.3-qtext (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.3-sip-qt3
 python2.3-qt3
 python2.3-qt3-gl
 python2.3-qtext

Failed to apply all changes! Scroll in this buffer to see what went wrong


Anyone else tried this?

Thanks

---

### Post by stodge on 2004-12-05
Ah never mind - I forgot that I installed SPE beforehand and this was causing a problem.

---

### Post by stodge on 2004-12-12
Are there any upgrades to the pyqt bindings in Ubuntu? The current version doesn't play fair with Twisted Matrix.

---

