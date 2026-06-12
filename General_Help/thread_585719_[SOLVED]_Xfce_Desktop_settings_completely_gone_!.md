---
title: "[SOLVED] Xfce Desktop settings completely gone !"
date: 2007-10-21
forum: General Help
---

### Post by perixx on 2007-10-21
I'm really in trouble....


I have installed Xubuntu 7.04 and added a few repositories (medibuntu, repoubuntu and some '...-sos-...' repo, in order to add multimedia abilities to the system. At some point I decided to change the default update repositories in Synaptic's packet manager from 'German' to 'Main', for I thought there might be more/newer updates availible. There wasn't a problem so far. After I've set up everything, I did set the default update repositories from 'Main' back to 'German' again - and did a second update in Synaptic. Shortly after that I shut down the system.

When I started the PC newly, the desktop was completely messed up, with all taskbars/systray/clock/applications button/symlinks for mozilla and were gone! Now I cannot access the menus, Internet and so on... What can be done?

perixx

---

### Post by perixx on 2007-10-22
It might be just broken profile-settings-links... is there some way to re-link the system to the old desktop settings ??
Someone has an idea?


perixx

---

### Post by perixx on 2007-10-26
PROBLEM SOLVED !!

[http://ubuntuforums.org/archive/index.php/t-415082.html](http://ubuntuforums.org/archive/index.php/t-415082.html)

Analog to this nifty problem-solver, all I needed to do was 
a) opening the Terminal > start 'xfce4-panel'
b) Applications > Settings > Settings Manager > ('Desktop/Workplace') > Tab ('Preferences') > check desired 'Show Icons for...' checkboxes
c) restart via Shutdown-Button

Voilà!


perixx

---

