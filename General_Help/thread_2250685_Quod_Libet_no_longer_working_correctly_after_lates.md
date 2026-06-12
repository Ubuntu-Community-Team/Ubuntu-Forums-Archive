---
title: "Quod Libet no longer working correctly after latest update"
date: 2014-10-30
forum: General Help
---

### Post by cscj01 on 2014-10-30
I am running Ubuntu 14.04.1 x64 with Gnome Flashback and kernel 3.13.0-39.  After the update that included the new kernel, Quod Libet will launch, but it will not open any window (I can see it running in System Monitor).  When I launch it in a terminal I get the following```
quodlibet
/usr/lib/python2.7/dist-packages/gi/types.py:259: RuntimeWarning: Mixin class UserDict.DictMixin is an old style class, please update this to derive from "object".
  RuntimeWarning)
```I have to kill the process no matter how I launch it.  Any thoughts?

---

### Post by cscj01 on 2014-10-30
Nevermind.  I just added the Quod Libet ppa and updated the software.  Problem fixed.

---

