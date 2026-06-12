---
title: "error message when trying to use windows xp in virtualbox"
date: 2007-05-29
forum: General Help
---

### Post by zach12 on 2007-05-29
hello
I'm having a problems with virtual box 
i just installed virtual box (i had some problems but i fixed them)made a virtual Machine (windows xp) and tryed to boot it when it tryed boot i got a error message here it is
(VirtualBox kernel driver not accessible, permission problem. Make sure that the current user has write permissions to /dev/vboxdrv by adding him to the vboxusers groups. Don't forget to logout to take the change effect.
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code:
0x80004005
Component:
Console
Interface:
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45})then it ends
thank

---

### Post by bodhi.zazen on 2007-05-29
You need to add your user to the vboxusers group.

---

