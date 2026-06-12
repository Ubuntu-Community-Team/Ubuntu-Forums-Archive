---
title: "run shell scripts from desktop"
date: 2007-01-28
forum: General Help
---

### Post by PetePete on 2007-01-28
how would i run a shell script from the desktop?

i've set it as executable but when i click on it nothing happens :(

(using kde btw)

would be alot quicker than opening terminal and typing ./scripts-name

---

### Post by PetePete on 2007-01-28
ok found a way, created link to application and called
 bash /home/pete/script 

but kde looks like it tries to load a program, with the icon on the mouse cursor, then stops after 10 seconds or so.. script runs fine but its quite annoying having to wait ... 

bit difficult to explain..

---

### Post by PetePete on 2007-01-28
heres a snapshot of what i mean.... u can see the mouse icon just above the taskbar window..

---

### Post by meng on 2007-01-28
1. Make sure the first line of your shell script reads:
#!/bin/bash

2. Make sure the script has been set to executable:
chmod a+x (name of file)

3. (I'm not a KDE user myself, but there may be a setting to run shell scripts on double-click without asking for confirmation.)

---

### Post by hal10000 on 2007-01-28
your shell script is probably running, but you have no chance to see where it's output (or input) goes to, because it might need a termial window.

A way to get it work may be to create a Desktop Icon:
1. Right click somewhere to your desktop
2. select New--->"Link to Program" (or something similar, translated from german)
3. Give a name you like, then go to "Application", under "Command" chose your shell script (INCLUDING PATH), then choose "Advanced Options" and mark "Run in Terminal", i guess this is the most important part because otherwise you won't be abls to see th output of your script. You may also choose "Do not close when command exits" to prevent the window from being closed immediately after your script ends.

Hope this helps.

---

### Post by PetePete on 2007-01-28
ahhh thanks
it was the "run in terminal" bit i missed ;)

they were still running though, as they modified some data when ran.

---

