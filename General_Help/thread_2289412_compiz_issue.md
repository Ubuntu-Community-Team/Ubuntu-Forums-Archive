---
title: "compiz issue"
date: 2015-08-03
forum: General Help
---

### Post by ariel8 on 2015-08-03
so a few minutes ago i ran ```
compiz --replace
``` in terminal, wanted to replace the current window manager.
i saw an error and a few warnings and then the process died.
i tried ctrl+alt+f1 to get to the terminal mode but the keyboard wont respond
i can still move the mouse and right click my desktop, but that's about it...
im afraid to reboot my pc, i dont want any harm done to my pc(well, anymore harm anyway...)

Update: i got to the system settings, not sure if there is much help there...

---

### Post by howefield on 2015-08-04
What window manager were you using before trying compiz--replace ?

I'm guessing you have decided what to do by now, 5 hours later.

Can you get a terminal with Ctrl + Alt + T and do a reboot via the terminal ?

---

### Post by grahammechanical on 2015-08-04
For the record, compiz --replace does not offer to replace Compiz with another window manager. It should restart Compiz. As far as I know from 12.10 onwards the command to restart compiz became

```
 dconf reset -f /org/compiz/
```

It it also my understanding that after installing an alternative window manager we restart and select the alternative window manager session at the login screen. That is what I did when I installed FVWM-crystal.

Regards

---

### Post by ariel8 on 2015-08-04
> **howefield said:**
> What window manager were you using before trying compiz--replace ?

I'm guessing you have decided what to do by now, 5 hours later.

Can you get a terminal with Ctrl + Alt + T and do a reboot via the terminal ?
as i said, i tried to get to terminal mode, i tried typing things, my pc didnt register any type of input from the keyboard.
there has been a blackout while i slept, the pc is back to norman. guess ill mark this as solved.

---

