---
title: "Incompatibility/but with windows 2000 and wubi."
date: 2007-05-23
forum: General Help
---

### Post by blackjackel on 2007-05-23
I have found the following incompatibility/bug with windows 2000 and wubi:

In windows 2000, you will not be able to select ANY option that has a drop down menu as all drop down menus in Wubi will be disabled. This is a windows 2000 specific bug.

I have tested this on 3 windows 2000 machines and 2 windows XP machines. All xp machines were able to access the drop down menus and change settings, all windows 2000 machines were not able to select ANY drop down menus.

So if you're using windows 2000, you'll have to stick with whatever default settings wubi has until this bug gets fixed. There are workarounds, such as installing wubi with the default settings then editing the wubi registry settings and reinstalling. This workaround does NOT work for all options, but does work for the drive which you want to install wubi.

---

### Post by ecology2007 on 2007-05-24
XPStyle has been reenabled yesterday, but i don't know if it is in minefield1.0.
Did you have the same bug with previous wubi version ?

[http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.9.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.9.exe)
[http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield1.0.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield1.0.exe)

What do you mean exactly by disabled ?
Empty, greyed, unclickable, crashing on clic, forced to default ... ?

A screenshot may help.
Specs of the computers too : RAM, number of drives, exact windows version (pro, not pro, server), and windows language.

Thanks forward.

---

### Post by flammingcowz on 2007-05-26
same thing with me, in windows 2000 pro it wouldnt let me drop down box things but i could scroll with the arrow keys

same computyer with xp let me drop down boxes

---

### Post by ecology2007 on 2007-05-27
I have found the bug,
Thanks for the report.

---

