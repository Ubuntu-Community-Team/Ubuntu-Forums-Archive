---
title: "[SOLVED] System wide problem (not sure how to describe it)"
date: 2007-12-21
forum: General Help
---

### Post by john91 on 2007-12-21
I was messing around some with compiz-fusion plugins and trying to install a few new ones, but compiling some of them failed.  After restarting the graphics with ctrl-alt-backspace, my panels are gone, desktop icons are gone, and i can't interface with my desktop at all except with the keyboard. Also, all my graphics settings have reverted to the default gnome settings.  I can start programs with the keyboard shortcuts just fine, and once within a program can interface with it like nothing has happened.  I realize what I'm posting here is very broad, but any help at all would be appreciated.

---

### Post by dondad on 2007-12-21
try bringing up a run dialog box (alt-f2) and typing:
```

metacity --replace

```

That should make your window manager metacity. See if that gets back at least some funcioonality.

---

### Post by staticvoid on 2007-12-21
my only advice:

reboot into recovery mode

then reboot again

if you go alt f2 and type in metacity --replace and then do it again and type gnome-panel

that should get you back some stuff... try some stuff. It should work. compiz shouldn't have the power to break your whole system.


sv

---

### Post by john91 on 2007-12-21
Alright, thanks.  I essentially did what you said, and it worked.   I'm still not sure what I did to cause this problem though.

---

