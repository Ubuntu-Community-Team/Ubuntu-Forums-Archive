---
title: "how to properly close terminal"
date: 2018-04-06
forum: General Help
---

### Post by seekertom on 2018-04-06
After using terminal, is there an elegant way to stop using it? like 'exit', or just 'x' out?

thanks, st:)

Ive been entering 'exit', then clicking the window 'x' to close it. From what you say, both contribute to a safe and happy Me. thanks, folks!

st

---

### Post by Dennis N on 2018-04-06
Ctl+D is possibly the most elegant. No mouse or typing needed.

---

### Post by vanadium on 2018-04-07
I didn't even know about Ctrl+D :-) Usually type exit. Also hotkeys to close the window (Alt+F4) or close gnome-terminal (if that is what you are using), i.e. Ctrl+q (which I disable system wide) are safe options: you will be warned if there is still a running process in that terminal. Clicking the x acts the same. So many options, which are all safe. Whether all are also elegant obviously is a matter of taste ;)

---

### Post by &amp;wP*!) on 2018-04-07
The safest way is **exit** command in the shell because the shell interpreter directly gets the command and tells you whether there are processes running spawned by the shell. The other way to close the terminal using the window icon "kills" the bash process. Maybe bash interpreter has an executable running, you never know. Therefore exit command is the safest.

---

