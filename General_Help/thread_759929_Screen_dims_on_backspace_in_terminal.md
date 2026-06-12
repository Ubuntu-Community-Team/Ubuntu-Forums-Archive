---
title: "Screen dims on backspace in terminal?"
date: 2008-04-19
forum: General Help
---

### Post by xvedejas on 2008-04-19
I have no idea why it does this.... Any help?


I'm using a custom-built desktop computer, and when I open a new window it is not dimmed but the rest of the screen still is.

---

### Post by ryanhaigh on 2008-04-19
I can't see an option in gnome-terminal but perhaps you are not using that but the only thing I can think of is the visual bell, there is a setting for this in gconf-editor and on my system it is not set.

---

### Post by xvedejas on 2008-04-19
Turns out it does this when I press backspace in any empty text area, not just the terminal.

---

### Post by ryanhaigh on 2008-04-20
The could still be the same issue as Im pretty sure the bell is used for this situation also. Are you using gnome (plain ubuntu) or kubuntu/xubuntu? Have you tried checking the setting in gconf-editor (gnome only).

If not to do this press alt-f2 and enter gconf-editor, press control-f and search for bell. There should be something about visual bell there if it is checked, uncheck it.

---

