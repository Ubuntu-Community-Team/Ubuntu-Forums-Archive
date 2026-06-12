---
title: "terminal command to read system wide mouse events (not xev)"
date: 2008-04-12
forum: General Help
---

### Post by duncan.hawthorne on 2008-04-12
is there a terminal command like xev, but better
xev spawns a new window, and can only capture mouse events in that window (or you can set it to capture mouse events from a specific other window)

would it be possible to capture the mouse events at a much lower levell,  as in reading directly from the device maybe. ideally something like using 
cat /dev/input/mice,
however for that the output is incomprehensible, and only seems to do mouse movement rather than click events

i would like a command which runs like a basically a system wide keylogger, but for mouse clicks. when you click the mouse anywhere (such as maybe even in a virtual terminal), the mouse events are read, and outputted into the terminal, and hopefully in a sensible fashion like
button 1
button 2
etc.  (something slightly more encoded but easy to work with would also be fine). if you can use xev to take events from all windows (hopefully including virtual terminals) this would be perfect, but i cant find such an option.

i want to take the output of this program and process it so that i can do things on specific mouse events system wide ie, when button 5 is pressed, run this command

any ideas? thanks :D

---

### Post by nanotube on 2008-04-13
i have an open source keylogger project written in python, which uses python-xlib to record keyboard and mouse events... if you want to take a look at the code, feel free, it's at
[http://pykeylogger.sourceforge.net](http://pykeylogger.sourceforge.net)

specifically you would be interested in looking at the pyxhook.py file.
it will take only minor modification to that file to produce a global mouse event logger as you want, so feel free to take a look at it, and ask me if you have any questions about the code.

since it uses xlib, it won't work on the console (virtual terminals), but it will work on anything that happens inside X.

---

