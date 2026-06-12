---
title: "Alt + PrtScr + R, E, I, S, U, B"
date: 2019-10-17
forum: General Help
---

### Post by kesetyan on 2019-10-17
In the past I have occasionally had to use the  Alt + PrtScr + R, E, I, S, U, B key combination to get out of a system freeze.  While this has always worked smoothly, the process does stretch (literally too) my keyboard fingering abilities. I wondered if it would be possible to create an executable script file, called up by a simpler to use key combination, to run the Alt + PrtScr + R, E, I, S, U, B key combination.  I believe that the R, E, I, S, U, B part of the combination requires a short pause between each keypress which I can't help but do with my limited keyboarding skills when trying to hold down both Ctrl and PrtScr while pressing the other keys in turn.  Would the need for a pause between key presses make what I would like to achieve impossible?

Thanks.

---

### Post by Holger_Gehrke on 2019-10-17
The Alt-SysReq-R-E-I-S-U-B is hardwired into the kernel. If the System has  frozen to the point where you need it, any program above kernel-level that's supposed to react to keystroke would be frozen, too.

Holger

---

### Post by kesetyan on 2019-10-17
Hi Holger,

Thanks for your very quick and clear and easy to understand response.  I'll just have to hope my aged finger joints remain sufficiently flexible for a few more years.

---

### Post by CatKiller on 2019-10-17
It's only the Alt key that needs to be held down throughout.

Hold Alt, and do SysRq followed by the kernel instructions that you need to send.

---

### Post by kesetyan on 2019-10-17
Hi Cat Killer,

Thanks for your input.  It certainly works and will ease my finger joints when I need to employ it - no more finger stretching exercises.

---

