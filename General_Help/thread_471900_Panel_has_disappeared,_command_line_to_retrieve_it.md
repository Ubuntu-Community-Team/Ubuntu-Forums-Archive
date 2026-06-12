---
title: "Panel has disappeared, command line to retrieve it?"
date: 2007-06-12
forum: General Help
---

### Post by jburgin on 2007-06-12
Howdy guys, 


I've got Ubuntu 6.04 (at least I think so, either way, it's Feisty w/Gnome) and I've had a recent problem of my desktop not completely loading with my computer boots. I recently installed Beryl and tweaked the settings and then set it to be my primary window manager when the system starts. Since then, my desktop does not completey load in that: 

Sometimes there are no desktop icons. 
Sometimes there is no "Application Taskbar", which I guess can be more accurately described as the bar at the bottom that all your applications are docked at. 
Sometimes there is no "Start Button panel". I know "Start Button" is a dirty word on a Linux forum, but that's the best way I can describe it, it's the bar where you can start and run all your programs and place quick launch icons. 

Either all 3 of these things happen or just one or two..the list goes on. I know Beryl is bug city with certain video cards, so I've come to accept this problem. But I am curious: 

Is there a way to start any of these panels from a terminal? I am able to access a terminal through right clicking, so is there a command I can type in to bring back my Start Button Panel and so forth? I know that you can hit Ctrl+Alt+Backspace to restart the X system, any other commands or tips you can offer is appreciated. 

Thanks in advance.

---

### Post by notwen on 2007-06-12
try typing ```
gnome-panel
```

---

### Post by jburgin on 2007-06-12
That worked, slightly. It didn't keep the theme, nor did it have any of my quick launch icons on there either. but at least I know how to pull up a menu bar in case mine ever dies.

---

### Post by kag on 2007-07-18
For the record, I'm having the same problem on Feisty. I've had Beryl installed since Feisty came out, and for the last week, my panels or the desktop icons are always not showing up when I log in. I looked in the logs and did not find anything I could understand.

---

### Post by strabes on 2007-07-18
Run this: ```
killall gnome-settings-daemon && gnome-settings daemon &
```

---

