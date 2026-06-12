---
title: "Anjuta Troubles"
date: 2005-08-21
forum: General Help
---

### Post by grenadadoc on 2005-08-21
I'm very new to Anjuta and am looking to use it to create C and/or C++ code to create an application front end for a MySQL database.  I used the Package Manager to install Anjuta 1.2.2 and as best as I can determine all the appropriate GLADE and GTK+ files that I could find.  Whenever I try to create an Anjuta project, basically accepting all the defaults, I get the following error messages:

A bunch of messages and then the following:
Makefile.am: installing './COPYING'
configure.in:110: required file'intl/Makefile.in' not found
configure.in:36: required file './ABOUT-NLS' not found
Makefile.am:6: required directory ./intl does not exit

./macros/autogen.sh:line 235: ./configure: No such file or directory
**Error**: 'automake' failed.  Please fix warning
(probably missing development files) and try again.

Please Help

Thanks in advance

---

### Post by Darko on 2005-09-03
You have to deselect the "Gettext" Option in the wizard. It is described in the [Anjuta Tutorial](http://www.anjuta.org/documentations/subpage/documents/C/anjuta-tutorial/index.html).

---

