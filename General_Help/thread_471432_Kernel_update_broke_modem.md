---
title: "Kernel update broke modem"
date: 2007-06-12
forum: General Help
---

### Post by emperorcezar on 2007-06-12
I have a Dell Inspiron e1505n. Yep, a dellbuntu. I did a kernel update today. This killed my modem. I've updated my kernel before without issue. I vaguely remember the system rebuilding the driver. I can't be sure though. Any ideas on how I can get the modem to work with the new kernel?

---

### Post by fragos on 2007-06-12
System-> Adminstration-> Network-> Connections tab.  Make sure the modem connection is checked.  Select "Modem connection" and click Properties to insure the dialup parameters are correct.

---

### Post by emperorcezar on 2007-06-13
It is a driver issue. All the settings are correct and my modem works under the previous kernel. Only if I boot into  2.6.20-16-generic will the modem quit working. Right now, when I need the modem, I boot into 20-15 and the modem works again. The modem is a Conexant and uses a restricted driver. 

Dell has information on the modem at [http://linux.dell.com/wiki/index.php/Tech/Modems](http://linux.dell.com/wiki/index.php/Tech/Modems)

---

### Post by fragos on 2007-06-13
I suggest you nudge Dell even though they provided information.  In all likely hood we're looking at a growing pain for Dell that will need to find a bettere way to integrate their restricted drivers into the Ubuntu update stream.  Making them open source would of course be best but they may not own that driver code.  Releases like 2.6.20-15 being upgraded to -16 may not require changes in driver source code but likely require a driver recompile.

---

### Post by highlighter on 2007-06-15
If you have a DellUbuntu PC , I suggest you call dell, they most have the driver you need...;)

---

