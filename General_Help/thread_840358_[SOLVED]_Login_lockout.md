---
title: "[SOLVED] Login lockout"
date: 2008-06-25
forum: General Help
---

### Post by saxuntu on 2008-06-25
I switched gdm themes and screwed it up some how. Now the cursor just spins and spins. Anyone know how to fix this? I'm going to try dorking around with LiveCD. It has both Mythbuntu (Xfce) and Ubuntu (gnome) installed.

Update: Tried > rm -rf .gnome .gnome2 .gconf .gconfd .metacity for both users. nothing. 
Tried copying same files from LiveCD. nothing

---

### Post by saxuntu on 2008-06-26
Figured out a solution:

Ctrl + Alt + F1 brings up a terminal and then login

> sudo /etc/init.d/gdm stop turns of gdm

> sudo apt-get purge gdm dumps gdm and configuration files

> sudo apt-get install gdm reinstalls

> sudo shutdown now restarts computer

---

