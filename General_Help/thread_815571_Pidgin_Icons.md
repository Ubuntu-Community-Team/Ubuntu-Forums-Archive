---
title: "Pidgin Icons"
date: 2008-06-01
forum: General Help
---

### Post by Camuso21 on 2008-06-01
So I downloaded a set of different icons (elegant brit icons from gnome-look) to swap out the standard ones for use in Pidgin. Whenever I try to exchange the ~usr/share/pixmaps/pidgin status and tray folders I get an error message that says Error: Permission Denied. Any thoughts, or easier way to change the icons in Pidgin?

---

### Post by FuturePilot on 2008-06-02
Open your Home folder and press Ctrl+H to show hidden files. Find the directory called .purple
Open that folder and you will see a folder called smileys. Place the folder containing the smileys you downloaded in there.

---

### Post by PinkFloyd102489 on 2008-06-02
Well if you're messing with the status and tray folders, it's obviously not smileys. Sorry to shoot you down FuturePilot.

You need to open Nautilus as root to do so. Probably the easiest way is to hit Alt+F2 and enter "gksudo nautilus" without the quotes. Then navigate to the Pidgin folder and do whatever you need to.

---

### Post by billgoldberg on 2008-06-02
I also use elegant brit and tried the elegant brit icons for pidgin, but the package isn't very complete:

---

