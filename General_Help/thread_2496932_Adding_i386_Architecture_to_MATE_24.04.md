---
title: "Adding i386 Architecture to MATE 24.04"
date: 2024-04-17
forum: General Help
---

### Post by mark bower on 2024-04-17
I am trying to get i386 architecture into the PC system, OS 24.04,  to support 32bit WINE.  Previously, and many many previous version of Ubuntu, I had no problems.  But now, the system will not accept the input.  The entries and results are,

sudo dpkg --add-architecture i386          - rtns no error msg and appears that command has been accepted

sudo dpkg --print-foreign architecture    -  rtns "error: unknown option --print-foreign-architecture

sudo dpkg --print-architecture                -  rtns AMD 64

sudo dpkg -architecture --list                  -  rtns AMD 64

Suggestions please tor resolve the problem

[Edit] Well I rear where i386 is now automatically installed on OS installation.  I went back and checked, and voila, i386 is present.  My problem is the incorrect syntax:  should have been "dpkg --print-foreign-architectures".  The plural of architecture is correct"

---

