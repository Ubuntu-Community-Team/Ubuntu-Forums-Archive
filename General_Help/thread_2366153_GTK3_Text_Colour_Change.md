---
title: "GTK3 Text Colour Change"
date: 2017-07-14
forum: General Help
---

### Post by Quarkrad on 2017-07-14
I was running mate 16.04 and could change the top panel text colour using gnome-color-chooser.  I've just upgraded to mate 17.04 to resolve some issues and tried to change the top panel text but it doesn't work.  I'm running 17.04 as my Desktop and just put 16.04 in a virtualbox session - both with gnome-color-chooser installed, and I can see changes text colour changes in 16.04 but 17.04 is completely unresponsive. Should gnome-color-chooser work in 17.04?

---

### Post by vasa1 on 2017-07-14
> **Quarkrad said:**
> ... Should gnome-color-chooser work in 17.04?
I'm guessing that that depends on the theme. Many themes have switched to a format using something called SCSS instead of plain CSS.

Edit: see [https://ubuntuforums.org/showthread.php?t=2322710](https://ubuntuforums.org/showthread.php?t=2322710)

---

### Post by Dennis N on 2017-07-14
> Should gnome-color-chooser work in 17.04?

MATE 16.04 still had some gtk-2 components. MATE 17.04 components were built gtk-3. gnome-color-chooser is an old tool from the days of the old Gnome Desktop in pre-Unity Ubuntu that changes gtk-2 settings, and I doubt it is going to function in 17.04.

Also in Mate 17.04, you will discover other stuff doesn't work. For example, I find I cannot use a bold-face application font for better clarity. Any bold (or italic) font is ignored except in gtk-2 based applications - few remain - the one that comes to mind is geany.

---

