---
title: "Linuxdcpp Through Automatix"
date: 2007-01-09
forum: General Help
---

### Post by esaym on 2007-01-09
I installed linuxdcpp with automatix and it seems to not have come with any icons.  None at all.  The icon that is supposed to be on task bar is nothing more then a solid tan square.  Not very pretty at all.  I have installed the program before through cvs and I didn't have this problem.  I am just trying to get out of messing with cvs.  Any fix this problem before?

---

### Post by thenetduck on 2007-01-09
I just tried installing linuxdcpp with Automatix2 and it installed the icon just fine. Could the icon theme you have be effecting it? 

 The Net Duck

---

### Post by esaym on 2007-01-09
> **thenetduck said:**
> I just tried installing linuxdcpp with Automatix2 and it installed the icon just fine. Could the icon theme you have be effecting it? 

 The Net Duck

Where did it install the icons to?  I have nothing in /opt/linuxdcpp

---

### Post by esaym on 2007-01-09
Ok I just updated the source through cvs and it is all good now.

```
cd /opt/linuxdcpp
cvs update -d
scons
scons install
```

Also the executable changes from ldcpp to linuxdcpp so you will have to update all your shortcuts.

The version that comes with automatix is mega OLD.  Lots new features and bug fixes in the latest version

---

