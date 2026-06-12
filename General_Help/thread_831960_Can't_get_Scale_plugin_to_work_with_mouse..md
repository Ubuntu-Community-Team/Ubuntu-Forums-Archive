---
title: "Can't get Scale plugin to work with mouse."
date: 2008-06-17
forum: General Help
---

### Post by anton on 2008-06-17
Sorry, I've already posted about this in the Desktop Environments section, before realizing that this is the more appropriate place . . .

I'm trying to set up Scale in Compiz-Fusion so that moving the mouse to the top right corner of any open window will show scaled-down versions of all current windows simultaneously.

Setting up a keyboard shortcut to do this was easy: I enabled "Scale" under "Window Management" and under Bindings I mapped "Initiate Window Picker For All Windows" to <Control><Alt><Up>. Works fine. But mapping "Initiate Window Picker For All Windows" to <TopRightEdge>Button1 doesn't work -- the window just gets greyed out as long as I hold in the mouse button.

Can anybody help?

---

### Post by ChameleonDave on 2008-06-17
What desktop environment are you using?

I encountered some bugs with screen edges in KDE 3, but it seems to be OK now that I'm on KDE 4.

---

### Post by anton on 2008-06-17
I'm using Gnome in Hardy.  Just tried with KDE 3.5 and it doesn't work either.

---

### Post by anton on 2008-06-17
Okay,I've figured this one out.  Apparently, one has to move the mouse pointer to the *desktop's* upper-right corner (the red log-off button).  I expected it to work from an application/folder's upper-right corner (the corner with the X).

---

### Post by techstop on 2008-06-17
> **anton said:**
> Okay,I've figured this one out.  Apparently, one has to move the mouse pointer to the *desktop's* upper-right corner (the red log-off button).  I expected it to work from an application/folder's upper-right corner (the corner with the X).

You can set that option to whatever you like in ccsm in the Scale plugin, Bindings tab, Initiate Window Picker option.

EDIT: Oops! I see you have already tried that in your OP.

---

### Post by ChameleonDave on 2008-06-17
OK, you should mark this thread as "[SOLVED]".

---

