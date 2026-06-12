---
title: "PS/2 Keyboard Problem - Modul problem"
date: 2007-05-15
forum: General Help
---

### Post by gajotres on 2007-05-15
Hi

Can anyone help me find module responsible for PS/2 keyboard. I am working on project thet
requires me to enable and disable PS/2[USB] keyboard and mice from time to time. Now I
know which modules are responsible for USB mouse, USB keyboard and for PS/2 mouse. But
I cant find one responsible for PS/2 mouse.

Now I have listed all keyboard related modules with: modprobe -l | grep -i keyboard but none
of them is listed in lsmod. I have tried to unload all 4 of them but none of them is responsible
for PS/2. I have also found that serial_raw is responsible for PS/2. I have unloaded it but
keyboard is still functional.

Now does anyone have more experience with this or knows any other way to disable keyboard?

:confused:

---

