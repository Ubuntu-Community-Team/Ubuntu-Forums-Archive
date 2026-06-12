---
title: "OpenOffice (OO) and ATI problem solution"
date: 2006-12-06
forum: General Help
---

### Post by cnbiz850 on 2006-12-06
I run Edgy and installed the latest ATI driver to use fglrx, but it turned out that OO programs crash with the ATI driver.  Saw similar problems in the forum from other people.  Just found out an easy a solution.  It is actually that OO, fglrx and scim are not compatible.  The following solves the problem:
1) scim-bridge and scim-qtimm.
2) modify /etc/X11/xinit/xinput.d/zh_CN and make GTK_IM_MODULE="scim-bridge" in the file.
3) if you have /etc/X11/Xsession.d/95xinput, do the same.
Restart and the problem goes away.

---

### Post by melanochaitus on 2006-12-21
It has solved my problem, which I have tried to solve for weeks.  Thanks a lot!

---

