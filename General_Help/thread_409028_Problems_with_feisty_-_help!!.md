---
title: "Problems with feisty - help!!"
date: 2007-04-14
forum: General Help
---

### Post by bootsbradford on 2007-04-14
I upgraded to feisty on thursday evening - no problems at all, worked fine! 
Booted up yesterday (friday) morning - worked all day and absolutely fine!

**Booted up yesterday (friday) evening, having jammed on boot-up the first time - big problems ever since...**

[LIST=1]
[*]Basic problem is that all application windows are missing the top and bottom of them (e.g. minimising icon, exiting icon)
[*]In many applications, e.g. firefox, xchat (though not all, e.g. open office) I cannot type anything!
[*]My windows switcher icon has vanished and cannot be reloaded
[/LIST]

This works is the case on all kernels in the boot-up menu

**I really need some help - ubuntu is absolutely useless in this state at the moment!**

---

### Post by Spr0k3t on 2007-04-14
Just curious... can you check to see if metacity is running or have you changed your windowmanager over to beryl?

---

### Post by bootsbradford on 2007-04-14
Haven't been using beryl. How do I check if metacity is running? I've looked in sessions and can't see it there

---

### Post by Spr0k3t on 2007-04-14
In a terminal, type in metacity and see what your results are.

---

### Post by LuxVoodoo on 2007-04-14
Another thing to check is System---->Preferences--->Desktop Effects.  I had both the Windows Switcher and no typing problems and both were because I had the Desktop Effects were enabled.  Uncheck both boxes and hit the enable button again to disable it (for some reason, that button doesn't say disable once it's enabled--hope that makes sense.  Once I disabled those desktop effects, everything went back to normal for me. But you know how Ubuntu is sometimes. One fix may not work for another.

---

### Post by Spr0k3t on 2007-04-16
```
metacity --replace
``` should get you fixed up if you have any further problems.

---

