---
title: "Trouble installing SVN version of libgpod"
date: 2008-06-24
forum: General Help
---

### Post by TMcKSmith on 2008-06-24
I've been looking into how to use my new iPod Classic (6th Gen) with Amarok and just read that the album artwork feature on the current version of libgpod is slow and makes an unusually large album artwork file (see:  [http://amarok.kde.org/forum/index.php?action=printpage;topic=15032.0](http://amarok.kde.org/forum/index.php?action=printpage;topic=15032.0)).  I'm trying to install the SVN version of libgpod (which apparently contains the fix) but am running to a dead-end error.  Can someone please help me?  Here's what I'm getting:

root@esper:~/libgpod# ./autogen.sh 
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.7...
  testing automake-1.10... found 1.10.1
checking for libtool >= 1.4.3...
  testing libtoolize... found 1.5.26
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.16.3
checking for intltool >= 0.25...
  testing intltoolize... found 0.37.1
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
checking for gtk-doc >= 1.0...
  testing gtkdocize... found 1.10
Checking for required M4 macros...
  gtk-doc.m4 not found
***Error***: some autoconf macros required to build libgpod
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?



Thanks.

---

