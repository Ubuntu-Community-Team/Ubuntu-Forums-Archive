---
title: "New X sessions use GTK1. Why not GTK2?"
date: 2007-07-14
forum: General Help
---

### Post by chadjohnson on 2007-07-14
Whenever I create a new X session manually from the tty

export DISPLAY=:1
X :1 vt8 &

and start a GTK program from the tty, the program shows up in the X session using GTK1. Why is this happening? How can I use GTK2 instead?

---

### Post by chadjohnson on 2007-07-14
Hmmm...when I run gnome-theme-manager from the tty, the window shows up with GTK2 (without changing any settings). And if I close this windows (by clicking Close) and then start another program, that other program also uses GTK2. This only works if I've started gnome-theme-manager, first.

Weird. Any ideas?

On another computer, I get the following message when I run gnome-theme-manager in the same manner:

[INDENT]Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.[/INDENT]

---

### Post by chadjohnson on 2007-07-16
bump...anyone?

---

