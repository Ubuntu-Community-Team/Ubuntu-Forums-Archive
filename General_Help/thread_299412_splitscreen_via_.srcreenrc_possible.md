---
title: "splitscreen via .srcreenrc possible?"
date: 2006-11-14
forum: General Help
---

### Post by SeriousJ on 2006-11-14
Hi, 

my .screenrc creates two windows on startup and starts a process in each of them. Now I want to display both windows on one screen - but without touching the keyboard. Does anyone know how to do this?


thnx 
Serious

---

### Post by ape on 2006-11-14
In your .screenrc file you want to do something like this:

screen -t "app1" 0
split
focus
screen -t "app2" 1

When you launch screen, you should now have a split screen with the first app running in the top window, the second app running in the bottom window.

Good luck!

--ape--

---

### Post by SeriousJ on 2006-11-14
It works! Thanks a lot.

---

