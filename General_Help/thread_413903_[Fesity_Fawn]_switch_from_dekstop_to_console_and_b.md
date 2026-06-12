---
title: "[Fesity Fawn] switch from dekstop to console and back &#8594; black screen"
date: 2007-04-19
forum: General Help
---

### Post by Skeletonix on 2007-04-19
**Hello**

It's not possible to turn from desktop (X) to console (ctrl+alt+f3) and back with enabled Compiz (nvidia). When I want to go back from console to desktop (ctrl+alt+F7) screen is black and not active. Only on way is to restore desktop, in console restart *gdm*.

If Compiz  is disabled everything work correctly !

Pleas what could be wrong ?:confused:

---

### Post by arsenic23 on 2007-04-19
Same thing in Beryl, only after switching back to the F7 window I could not leave it and was forced to manually restart my machine.

---

### Post by g8m on 2007-04-19
Yup, same thing here, had to restart. Black screen, only thing that works is the mousepointer.

---

### Post by Cicatrix on 2007-04-19
It works for me with beryl after a delay of about a second...

perhaps when in X (after pressing ctrl+alt+f7) a restart of x will help? (ctrl+alt+backspace)

---

### Post by Skeletonix on 2007-04-19
if X is restarted (or console is switch back to 3th windows) until 5s it´s OK, dekstop shoul be restarted  ... but If I wait some time only posibility is pusch restart button (screen is black and curosor active, keybord has no respons )

---

### Post by Abandon on 2007-04-19
Hmm..when i want to switch back from another active account op my desktop machine, than the same problem  occurs. Black screen, no working keyboard. So .. we found a bug!

---

### Post by Skeletonix on 2007-04-19
It is know reported ... [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/107786](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/107786)

---

### Post by Skeletonix on 2007-04-20
the solution is far away !

---

### Post by Lillo on 2007-05-04
Confirm the bug and the workaround

Disabled in Compiz settings the sync_to_vblank option
(I also disabled in nvidia-setting)

Tnx Skeletonix!

---

