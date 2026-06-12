---
title: "How can I install Xlib?"
date: 2008-01-07
forum: General Help
---

### Post by ehdtkqorl123 on 2008-01-07
I am trying to create a program using C and Xlib.
However, if I try to execute some C code on terminal, it creates errors related to header.
It seems like header is not loaded properly..
How can I install Xlib so that it works perfectly?
Someone please help me! Thank you!

---

### Post by bettlebrox on 2008-01-07
Sounds like you might need the xorg development package?
This will show you what the package contains:
[INDENT]aptitude show xorg-dev[/INDENT]

The description is:

[INDENT] X Window System design documentation, manual pages, library reference works, unstripped and static versions of the shared libraries, C  header files, and special versions of libraries available only in static form (with and without PIC symbols included) are supplied by the packages depended on by this metapackage. [/INDENT]

This command will install the package:
[INDENT]sudo aptitude install xorg-dev[/INDENT]

---

