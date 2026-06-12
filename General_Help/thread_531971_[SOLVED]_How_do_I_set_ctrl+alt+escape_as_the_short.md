---
title: "[SOLVED] How do I set ctrl+alt+escape as the shortcut for xkill on GNOME?"
date: 2007-08-22
forum: General Help
---

### Post by wersdaluv on 2007-08-22
On KDE, control+alt+escape is xkill. On GNOME, I made a force quit panel shortcut as an alternative for xkill, but I still prefer control+alt+escape.

On Configuration Editor, under /apps/metacity/global_keybindings, I set run_command_3 as <Control><Alt>Escape. Under /apps/metacity/keybinding_commands, I set xkill as the value. After doing that, I pressed ctrl+alt+esc, but xkill was not activated. A box just appeared and surrounded my upper panel or my whole desktop.

How do I set ctrl+alt+esc as xkill on GNOME?

---

### Post by ironfistchamp on 2007-08-22
Just an idea, is the key actually called Escape? I have used (what I believe is) that method to assign xkill to Ctrl+Alt+X so the only thing I can think of is it not recognising the name "Escape"
 
Then again I could be talking out of my backside.
 
HTH
 
Ironfistchamp

---

### Post by aysiu on 2007-08-22
Are you using Beryl or Compiz?

---

### Post by wersdaluv on 2007-08-22
> **aysiu said:**
> Are you using Beryl or Compiz?

Just Metacity.

:KS

---

### Post by aysiu on 2007-08-22
> **wersdaluv said:**
> Just Metacity.

:KS
Can you post a screenshot of what this box looks like that appears?

---

### Post by wersdaluv on 2007-08-23
There you go

:KS

---

### Post by wersdaluv on 2007-08-23
It works now. 

I guess, I just had to reboot. 

:guitar:

---

