---
title: "Making Windows a bit easier to accomidate..."
date: 2006-08-18
forum: General Help
---

### Post by Patrick-Ruff on 2006-08-18
hey all, is it possible to make it so a part or majority of a window can be under a panel? I mean I noticed that it appears to be impossible to make windows go under the 2 panels, but you can make half the window go to the side and all that, but I mean its a real pain because it makes it appear as I don't have as much workspace you know? so is it possible to make this happen? I know its kind of hard to describe but if you want a screenshot of what I'm talking about I can post it (it would be a windows screenshot of course).


thanks to those that reply..

---

### Post by Patrick-Ruff on 2006-08-18
ok fine ignore this thread.... *sighs* please people if I lack in information TELL me lol.

---

### Post by MarinaraOfDeath on 2006-08-18
Have tried setting the panels to auto-hide? Right-click a panel, then select the Properties menu. See if it gives you the effect you like. If it does, you can dig into the setting in gconf-editor (run in terminal) to find the settings to minimize how many pixels of a panel stay on screen when it's hidden.

---

### Post by Patrick-Ruff on 2006-08-19
nah that's not what I was thinking, because even then the windows still get locked at the bottom of the screen, rather then being able to go beyond the screen.

---

### Post by Tomosaur on 2006-08-19
Uhh - you can make windows go behind the panels:

---

### Post by Patrick-Ruff on 2006-08-19
well it doesn't let me do that, apparently....

---

### Post by Patrick-Ruff on 2006-08-19
also, I'm using XGL/Compiz, you think that could have anything to do with it?

---

### Post by Tomosaur on 2006-08-19
Ahh, maybe. You do need to 'push harder' on the windows to get them to go behind the panels though, you know. They do snap to the panel at first, but if you keep pushing them, they should carry on moving.

I'm not running XGL/Compiz so I can't confirm your problem sorry.

---

### Post by Patrick-Ruff on 2006-08-19
lol I've pushed hela hard beyond reason, it doesn't go.

---

### Post by MarinaraOfDeath on 2006-08-21
Well, if what you want is a window that is larger than the screen, try unmaximizing the window. Then you move it over so that part of it is off-screen, let go, grab the edge onscreen and resize.

---

### Post by spockrock on 2006-08-21
ok open terminal

gconf-editor

apps>compiz>plugins>move>allscreens>options>

there are two options constrain_y_top/bottom uncheck then and you will be able to do it now.

---

