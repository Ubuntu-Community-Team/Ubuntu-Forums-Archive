---
title: "Close Pidgin with the &quot;escape&quot; button"
date: 2008-06-13
forum: General Help
---

### Post by :overclock: on 2008-06-13
I'm sure this question has been asked before but I couldn't find anywhere a clear explanation about this. I want to know how change the window closing command from ctrl+w (I'm not sure if it's like that) to esc. 
Ubuntu 8.04 and have Pidgin 2.4.1 installed.

---

### Post by aysiu on 2008-06-13
I don't think you can. You might be able to map the command ```
killall pidgin
``` to the Escape key using ```
gconf-editor &
``` and Apps > Metacity, then Global Keybindings (Escape) and Keybinding Commands (killall pidgin).

I'm not sure if it's a good idea to kill it every time, though, instead of exiting cleanly.

---

