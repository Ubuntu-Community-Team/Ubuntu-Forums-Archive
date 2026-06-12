---
title: "Screensaver Problem"
date: 2006-12-12
forum: General Help
---

### Post by alexbOrsova on 2006-12-12
Hi all, I need help. Every time I open up the Screensaver panel from System->Preferences->Screensaver, my system hangs. Is there any way I can change the screensaver from the command line? Because every time my screensaver comes on, when the session goes idle, my computer hangs. Thank you in advance, Alex.

---

### Post by kd7swh on 2006-12-12
I don't know about changing it from the command-line, but that sounds like a bug. Are you using edgy or dapper?

---

### Post by alexbOrsova on 2006-12-13
I'm using Ubuntu Dapper 6.06.1 LTS.

---

### Post by alexbOrsova on 2006-12-14
I'm still having these problems, but I've just discovered that my system also hangs when I try to play any 3D games (which I should be able to do with a Radeon Pro 9800 gfx card, right?).

---

### Post by DroG on 2006-12-15
I'm having the same problem, when the screensaver kicks in the system hangs - when I go to preferences-screensaver to set the screensaver to none, the system hangs.  Hasn't anyone got a newby-friendly work-around/cure?  Can I uninstall the screensavers altogether?  ](*,)

---

### Post by ghepardo on 2006-12-15
Drog and alexBorsova I had these problems and I solved in this way.

I installed the lastest nvidia drivers with the ENVY script from Alberto Milone.

In the nvidia xserver settings (under system tools)  I disabled the "allow flipping" and the "sync to vblanc".

After these operations I solved the issue..

I hope this helps you.

---

