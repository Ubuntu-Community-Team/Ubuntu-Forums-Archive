---
title: "How to change already present keyboard layouts?"
date: 2013-01-15
forum: General Help
---

### Post by zettez on 2013-01-15
EDIT:
Solved! [This]("http://superuser.com/questions/537097/how-do-i-change-the-actual-x-server-keyboard-layout-keys") worked.

Not sure if I posted in the right section.

I use the Swedish (Dvorak) layout and it has worked very well. Some time ago I bought a new keyboard which with the current layout is missing the pipe key which I frequently use. Is there any way to change the current keyboard layout without hacks and stuff to create a pipe at a key event? I know I can somehow get the key code from any key so that will not be any difficulties.

---

### Post by rnerwein on 2013-01-15
> **zettez said:**
> Not sure if I posted in the right section.

I use the Swedish (Dvorak) layout and it has worked very well. Some time ago I bought a new keyboard which with the current layout is missing the pipe key which I frequently use. Is there any way to change the current keyboard layout without hacks and stuff to create a pipe at a key event? I know I can somehow get the key code from any key so that will not be any difficulties.
hi
i think if you open the dash-board there must be an applikation "keyboard" (mine is german and called tastaur). i think the the way you can manage your behavior.
cheers

---

### Post by zettez on 2013-01-16
> **rnerwein said:**
> hi
i think if you open the dash-board there must be an applikation "keyboard" (mine is german and called tastaur). i think the the way you can manage your behavior.
cheers

I may only change shortcuts there and what I want is to change a specific key to produce another symbol. I might be able to produce a shortcut that runs a script that outputs the desired key but that seems too much of a hack. I am sure there is a file that contains the mappings for the layout and the keycodes used. By merely entering that file and change from say keycode 1 to 2 it will produce another symbol. Are the keyboards integrated in the X server code or are they stand alone?

---

