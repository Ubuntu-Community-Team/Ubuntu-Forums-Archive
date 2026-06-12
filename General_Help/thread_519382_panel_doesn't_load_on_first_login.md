---
title: "panel doesn't load on first login"
date: 2007-08-07
forum: General Help
---

### Post by patmalcolm91 on 2007-08-07
hello, i'm running ubuntu feisty with beryl and avant window navigator (AWN). Whenever i log on for the first time, avant half-loads (the bottom fifth of the screen is black behind the dock and no icons), and my top panel doesn't show up, i can still move my mouse and use the desktop icons though. then if i log out again (by hitting my computer's power button, and selecting log out from the window) and log back in, the panel loads and then avant opens and everything is fine. does anyone have any idea why this might be?

*note: when i go to the terminal and type "gnome-panel" it says that there already is a panel open, and won't launch

---

### Post by Universered on 2007-08-07
ALT+F2. In the box type xfce4-panel

---

### Post by patmalcolm91 on 2007-08-07
the Alt+F2 thing doesn't do anything, i have gnome-panel installed, not xfce4-panel, and i don't want to have to type something every time i log on just to have a panel, i want to actually fix it. i believe it is Avant causing this problem, but i don't want to get rid of it, because kiba-dock freezes my whole system up, and there is no other good looking panel for gnome that i've come across, I've thought about switching to KDE and using KXDocker. does anyone have any suggestions or help??? it gets really old to have to log on, log off and log on again every time i want to use my computer.

---

### Post by Universered on 2007-08-07
ok go to google.com and find whatever command starts up the 'gnome-panel' ALT+F2 it and when u are logging out or restarting ur macine (whatever ur going to do) **save ur session and exit**

-ur good looking gnome-panel shouldn't disappear any longer
gd luck

---

### Post by patmalcolm91 on 2007-08-07
thanks, that worked. it was still running a little glitchy though, so i searched around a bit more, and i found the command: "killall gnome-settings-daemon && gnome-settings daemon &" , which seems to have done the trick.

---

### Post by Universered on 2007-08-08
i'm glad :)

---

