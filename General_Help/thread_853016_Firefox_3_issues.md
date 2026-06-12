---
title: "Firefox 3 issues"
date: 2008-07-08
forum: General Help
---

### Post by amazoohwawa on 2008-07-08
when Firefox 3 freezes i use the force quit button to quit. however when i try to relaunch Firefox 3 i get this message: "Firefox is already running, but it's not responding. To open a new window, you must first close the existing Firefox process, or restart your system." when i try to restart the system will not restart and i have to force shut it down by pressing the power button for a few seconds and then restart again.

does anyone know why im having the problem and can i be solved???

help is always appreciated

---

### Post by Voorhees1979 on 2008-07-08
Try and type "killall firefox" into a terminal. Sometimes firefox takes a few seconds to stop after a force quit.

killall is a handy cmd if something crashes.

---

### Post by amazoohwawa on 2008-07-08
i tested when firefox is working, not frozen and it says: "no process killed"

does it have to be crashed in order for killall to work???

---

### Post by alberto ferreira on 2008-07-08
Type :
pkill firefox

---

### Post by nikgare on 2008-07-08
sudo killall firefox-bin

---

### Post by Voorhees1979 on 2008-07-08
That is odd. When I have firefox running all I have to do is open a terminal and type "killall firefox" and it will shut down stright away.

---

### Post by aysiu on 2008-07-08
If ```
killall firefox
``` doesn't work, try ```
killall firefox-bin
``` (no *sudo* prefix is necessary for that command).

---

