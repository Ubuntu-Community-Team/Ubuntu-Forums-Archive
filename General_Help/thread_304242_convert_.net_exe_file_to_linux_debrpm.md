---
title: "convert .net exe file to linux deb/rpm?"
date: 2006-11-21
forum: General Help
---

### Post by gammyhand on 2006-11-21
I have written a piece of software on Windows in dot net.

Is there a program for ubuntu that will convert this into a program that will run on linux?

I have seen grasshopper for windows ([http://dev.mainsoft.com/Default.aspx?tabid=45](http://dev.mainsoft.com/Default.aspx?tabid=45))

but was hoping for a free version on linux?

---

### Post by skymt on 2006-11-21
The first step is to find out if it will compile and run on [Mono](http://www.mono-project.com/). If it will, you can package it the normal Linux way. IBM has a nice short tutorial for [.deb](http://www-128.ibm.com/developerworks/linux/library/l-debpkg.html)s, and the official RPM site has their own howto for [.rpm](http://www.rpm.org/RPM-HOWTO/build.html)s.

---

### Post by gammyhand on 2006-11-22
Thanks, will look into it.

---

