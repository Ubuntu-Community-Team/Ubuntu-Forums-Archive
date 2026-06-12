---
title: "Help my panels have vanished!"
date: 2007-06-17
forum: General Help
---

### Post by Lozz on 2007-06-17
I don't know why this has happened but I got up this morning switched on my computer & the only panel I had on my desktop had vanished. Now I find that I can't do anything to open another as the only way I know to make one is by right clicking on one which already exists. I should point out that I am totally new to this which probably doesn't help but if someone could tell me 1) the launcher command to open terminal & 2) the terminal command to make a panel I would be very grateful.

---

### Post by NikoC on 2007-06-17
Maybe this could work, assuming that you are using gnome:
```
alt + f2
```
This will open a box from which you can run any command.
Than type:
```
gnome-panel
```
i.e. the command for starting the 'normal' top panel

Good luck

---

### Post by Lozz on 2007-06-17
Thanks for that but I'm afraid things seem to be very strange when I entered the command you gave I got this message...

"I've detected a panel already running,
and will now exit."

Any ideas? Oh & I'm running gnome, beryl & kiba dock I probably should have said that in my first post.

---

### Post by Lozz on 2007-06-17
I've managed to fix it now. In case this happens to anyone else here's what I did to solve the problem. In the home folder is a hidden folder called .gnome2 delete it & then use ctrl+alt+backspace to log out & back in again. Upon login the panel should return.

---

