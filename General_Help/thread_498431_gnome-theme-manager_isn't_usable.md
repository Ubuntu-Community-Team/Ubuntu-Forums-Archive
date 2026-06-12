---
title: "gnome-theme-manager isn't usable"
date: 2007-07-11
forum: General Help
---

### Post by lugburz on 2007-07-11
I tried to change my gnome theme using the gnome-theme-manager. The application is open correctly but if I try to do anything: scrolling the theme list, clicking to add or remove a theme, doing anything, the windows appear stuck, the processor go to 100% for the gnome-theme-manager process but the window doesn't respond.

Any idea?

---

### Post by mkis62 on 2007-07-20
> **lugburz said:**
> I tried to change my gnome theme using the gnome-theme-manager. The application is open correctly but if I try to do anything: scrolling the theme list, clicking to add or remove a theme, doing anything, the windows appear stuck, the processor go to 100% for the gnome-theme-manager process but the window doesn't respond.

Any idea?

Same problem here: gnome-theme-manager opening ... after that all freezing, except the mouse pointer (without any effects). Reboot is possible only after Ctrl+Alt+F1 (or only pushing the reset).
BTW, I'm using Compiz Fusion on i910GML, and all plugins running OK...
Running **metacity --replace** causes the same system freeze.
The only working way to change themes is (for me, at this time :confused:) : disable the **compiz --replace** and **emerald --replace** in *Sessions*, reboot and in *Terminal*: **metacity --replace** (no windows decorations after reboot), enable the **compiz --replace** and **emerald --replace** in *Sessions*, reboot... ](*,)

edit>
Another way to change themes: *Beryl Manager *> switch to metacity, *Theme *> change theme, *Beryl Manager* > switch back to compiz, c**lose Beryl Manager**, then run **compiz --replace**. 

Reinstalled Compiz fusion, Beryl, Emerald, Gtk themes... nothing changed.

...perhaps is a bug in CF... and will be resolved after some updates? Or is something else wrong?

---

### Post by lugburz on 2007-07-22
I solved in kind of window method: I recreated my home from the the scratch and this fixed the problem. I don't think this is the best solution but works and is pretty fast.

(K)Ubuntu are losing some points for me :-( to many strange behaviours :confused:

---

