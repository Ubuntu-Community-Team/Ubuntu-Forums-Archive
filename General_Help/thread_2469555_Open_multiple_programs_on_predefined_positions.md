---
title: "Open multiple programs on predefined positions"
date: 2021-12-02
forum: General Help
---

### Post by uros-likar on 2021-12-02
I want to create bash file which will open multiple programs on my dual monitor setup and I want that each program is positioned at specific position and specific size. I don't have a clue where to start to setup something like it. Do I need to install some additional programs or I can do it by default kde/ubuntu  ?

Thanx for advices

---

### Post by dragonfly41 on 2021-12-02
Probably a bash file which uses xdotool will meet your requirements.
There are alternative ways I have used but xdotool is flexible.

---

### Post by TheFu on 2021-12-03
Many programs accept a -geometry option on the command line which will set the upper left point and the X:Y width and height from that point.

For example, this is what I use to setup Firefox to a specific location+size along with 2 remote terminals (lower left and lower right corners) for a specific workflow I use weekly.

```
# Change to desktop 2
xdotool set_desktop_viewport 1980 0
sleep 1s;

# move Firefox to a specific place and size
xdotool search --name "Mozilla Firefox" windowmove 100 143
xdotool search --name "Mozilla Firefox" windowsize 1612 663

sleep 1s;
# Open 2 xterms on the bottom on istar
XTERM_OPTS="-u8 -fs 12 -fa Monospace -sb -fg green -bg black"
xterm -geometry 80x15+0-0 $XTERM_OPTS -e ssh -X istar &
xterm -geometry 80x15-0-52  $XTERM_OPTS -e ssh -X istar &
```

Firefox doesn't accept -geometry options, but almost every X/client program does. Programmers have to to out of their way to prevent that capability - which says something about Mozilla.

---

### Post by uros-likar on 2021-12-05
Thanx for info and directions I need to take. I'll try it soon.

---

