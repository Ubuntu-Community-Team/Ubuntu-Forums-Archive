---
title: "xmodmap execute a script"
date: 2008-03-18
forum: General Help
---

### Post by Danners on 2008-03-18
Does anyone know how/if it's possible to get xmodmap to execute a script?

Basically I'm looking to set a button on my laptop to run a script to rotate the screen and reconfigure the buttons.

Cheers!

---

### Post by scottro on 2008-03-18
It depends upon the commands.  The xmodmap program takes a limited set of commands, e.g., keycode x = y add Modx = key y and the like .

If it's commands like that, you can make whatever file you want and then run xmodmap myfile.

If the commands aren't commands that xmodmap recognized, it will respond with unknown command type errors.

---

### Post by Danners on 2008-03-18
Thanks for the response, was looking to run a set of commands on one keypress, namely xrandr -o left && xsetwacom set stylus Rotate CCW plus 6 xmodmap -e ... commands. Sounds like that's not going to be possible within xmodmap.

---

