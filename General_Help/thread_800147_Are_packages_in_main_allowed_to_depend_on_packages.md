---
title: "Are packages in main allowed to depend on packages in universe?"
date: 2008-05-19
forum: General Help
---

### Post by CrazyGuy123 on 2008-05-19
Are packages in main allowed to depend on packages in universe?

"eric" (in main) seems to depend on "libqscintilla2" (in universe) - is that right?

---

### Post by Monicker on 2008-05-19
EDIT:  Disregard previous.  Eric also seems to be in universe.


```
arkaic@limbo:~$ sudo apt-get -s install eric
[sudo] password for arkaic:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  bicyclerepair libqscintilla2-3 libqt4-core libqt4-gui python-qscintilla2 python-qt4 python-qt4-common python-sip4
Suggested packages:
  vim-python idle pymacs pyqt4-dev-tools python-doc python-profiler qt4-assistant qt4-designer qt4-doc qt4-linguist ruby python-qt4-dbg
Recommended packages:
  eric-api-files libqt3-i18n qt4-qtconfig
The following NEW packages will be installed:
  bicyclerepair eric libqscintilla2-3 libqt4-core libqt4-gui python-qscintilla2 python-qt4 python-qt4-common python-sip4


arkaic@limbo:~$ apt-cache policy eric
eric:
  Installed: (none)
  Candidate: 4.1.1-1ubuntu1
  Version table:
     4.1.1-1ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/universe Packages



arkaic@limbo:~$ apt-cache policy libqscintilla2-3
libqscintilla2-3:
  Installed: (none)
  Candidate: 2.1+snapshot20070923-1ubuntu1
  Version table:
     2.1+snapshot20070923-1ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/universe Packages

```

---

