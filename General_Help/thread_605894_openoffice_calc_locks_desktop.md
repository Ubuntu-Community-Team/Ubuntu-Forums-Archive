---
title: "openoffice calc locks desktop"
date: 2007-11-07
forum: General Help
---

### Post by starfry on 2007-11-07
Hi,
I have OpenOffice 2.2 running on Feisty.
I have experienced more than once my enter desktop freezing, except the mouse pointer, while using open office. The only solution is to reboot. Any help appreciated?

---

### Post by oilchangeguy on 2007-11-07
> **starfry said:**
> Hi,
I have OpenOffice 2.2 running on Feisty.
I have experienced more than once my enter desktop freezing, except the mouse pointer, while using open office. The only solution is to reboot. Any help appreciated?

[http://support.openoffice.org/index.html](http://support.openoffice.org/index.html)

---

### Post by dabl on 2007-11-07
Did you try Ctrl-Alt-Backspace, to restart the X server?  If that doesn't work, then, before you press that power button, do:

```
Alt-SysRq  r  s  e  i  u  b
```

Hold down Alt and SysRq, and then, in sequence, press the other letters. Remember this:

_R_aising _S_kinny _E_lephants _I_s _U_tterly _B_oring

It is a way to do a graceful shutdown when the X server is hung up.

Of course, that doesn't fix OO Calc ....   :lolflag:

---

