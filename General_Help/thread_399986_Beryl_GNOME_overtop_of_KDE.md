---
title: "Beryl: GNOME overtop of KDE"
date: 2007-04-03
forum: General Help
---

### Post by freedomorfire on 2007-04-03
Not a huge issue, but still an issue.

Whenever I load Beryl as my window manager, it also loads GNOME overtop of my KDE desktop. I still have the KDE toolbars and settings, but my desktop background/icons are from my previous GNOME environment.

I can tell its overtop because using the transparent cube, i can see the wallpaper/icons from the KDE desktop.


any ideas?

---

### Post by ndefontenay on 2007-04-03
That is really weirf. Do you have both KDE and Gnome installed right now?

What if you uninstall Gnome? Just to try...

---

### Post by hikaricore on 2007-04-03
Are you by any chance using nautilus as your file browser instead of konqueror?

This could be causing issues with beryl.

---

### Post by freedomorfire on 2007-04-03
No, everything in KDE works fine (including konquerer).  It's only the GNOME desktop that loads with Beryl.

---

### Post by freedomorfire on 2007-04-07
Can anyone help?

---

### Post by freedomorfire on 2007-04-08
fixed by upgrading to 6.10 thnx anyways

---

### Post by shinda on 2007-04-12
I've been having the same problem except I'm using Edgy, so if anyone could help it be appreciated..

---

### Post by shinda on 2007-04-13
Turned out the problem wasn't a specificly beryl based rather had more to do with nautilus being loading by KDE. Took it out the lines referring to nautalius from ksmserverrc file (~/.kde/share/config/ksmserverrc), and problem solved.

---

