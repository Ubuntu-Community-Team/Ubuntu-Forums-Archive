---
title: "broke ubuntu by installing a theme"
date: 2007-01-04
forum: General Help
---

### Post by zmuth734 on 2007-01-04
I accidentally dragged a mouse cursor theme to the gnome theme manager and applied it and now I have no panels and icons and no desktop.

When starting ubuntu (after logging in) I get the ubuntu splash screen thing and I hear the drums.  The splash screen stays up and I have no panels or desktop icons.

Please help me!!

I was thinking maybe use gtk-theme-switch from the recovery command line?

---

### Post by zmuth734 on 2007-01-05
please someone helppp :(

---

### Post by d3v1ant_0n3 on 2007-01-05
Load up a 'failsafe' session (from the sessions menu at the log in screen). go to /home/.themes (you'll have to show hidden files) and delete the offending themes' folders. All should be well with the world.

---

### Post by Falcorian on 2007-01-05
I've installed some themes that have messed me up in the past, and I've fixed it as follows:

In terminal (ctrl + alt + F1) I log in and remove the theme from my ~/.theme folder. That makes Gnome go back to it's default theme when you next log in.

You may need to restart, I don't remember exactly.


I hope that works for you! Good luck!

---

### Post by zmuth734 on 2007-01-05
> **d3v1ant_0n3 said:**
> Load up a 'failsafe' session (from the sessions menu at the log in screen). go to /home/.themes (you'll have to show hidden files) and delete the offending themes' folders. All should be well with the world.

the fail-safe gnome session at login worked for me!

i went to system>preferences>theme and removed the mouse cursor icons (you're not supposed to install mouse cursor icons there) under theme details > icons.  It made the mouse cursors into icons for my ubuntu and it was going crazy.  Thanks!!!  I'm so happy I didn't have to reinstall.

---

