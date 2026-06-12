---
title: "help!"
date: 2008-02-12
forum: General Help
---

### Post by mountainman_chuck on 2008-02-12
.....I dunno what happened, but there is no window manager; there isn't a window border to click on minimize or restore or close. what do i do?

---

### Post by x1a4 on 2008-02-12
Restart the window manager.  Press Alt+F2 to open the 'Run' dialog and type the file name for your window manager.  I haven't used Gnome for a long time (and don't have it installed now) so I don't remember what Gnome's WM executable is, but if you look in /usr/bin/ you should have a file called 'metacity' (Metacity is the name of Gnome's WM) (or have 'metacity' in its name) or perhaps something like 'gnome-window-manager' or 'metacitywm' or 'gnome-wm', something with 'wm' at the end of its name.  Use a terminal to look for the files and check the man page of anything that looks like it might the the Gnome Window Manager.  

Once you find it, run it from the Run dialog or from the command line with an ampersand (&) at the end to fork it away from the terminal.

---

