---
title: "Beryl gtk theme problem?"
date: 2006-10-26
forum: General Help
---

### Post by Rackerz on 2006-10-26
The problem is I want to have the Ubuntu Human Looks default GTK theme as my theme in Beryl but it wont change to that theme, it's just a theme that looks like Win98 and the window title bar is blue. Why wont the GTK theme apply itself when I'm using Beryl?

---

### Post by dbott67 on 2006-10-26
If I understand your problem correctly, I think that you need to use the theme manager in Beryl.

When you click on the Beryl icon, do you get an option to change the theme?

(I'm not in front of my laptop right now, so I can't tell you the exact steps).

-Dave

---

### Post by PriceChild on 2006-10-26
Beryl uses its own themer.

ensure you have "emerald-themes" installed, then System>Preferences>"Emerald Theme Manager"

Select your theme from there :)

---

### Post by Rackerz on 2006-10-26
Yeah. I've done that and all it does is change the title bar to the orange look but not the theme itself, not that taskbar or anything :(.

EDIT: Found the solution, you have to put these into the startup programs.

> gnome-settings-daemon

And (I think)

> gnome-session-properties

---

