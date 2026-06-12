---
title: "revert to default panels"
date: 2008-04-27
forum: General Help
---

### Post by sept298901 on 2008-04-27
well, i am really excited that i got linux working for the first time.  i have never used linux before but i figured i would give it a shot... then i accidentally deleted the top panel.  i tried getting it back by adding a panel but it didn't really work the way that i hoped.  i was wondering if there was a way to revert back to the default desktop environment (and get that top panel back w/ all my utilities) without re-installing xubuntu.  thanks

---

### Post by MontyV on 2008-04-28
Wow I thought I was the only one.  I did the same thing trying to move panels around and realized I deleted the panel instead of just moving it, which is what I intended.  Looking for clues also here.

---

### Post by nbayiha on 2008-04-28
I actually got the same problem, and till now i didn't succeed to get my panel back the way it was when i install the system. But one by one i put back those icon i need the most.

---

### Post by sisco311 on 2008-04-28
Xubuntu (Xfce4):

From the terminal:
```
rm -fr ~/.config/xfce4/panel
``````
killall xfce4-panel
```Alt+F2 -> xfce4-panel

For Ubuntu (Gnome) users:
```
rm -rf ~/.gconf/apps/panel
``````
killall gnome-panel
```Alt+F2 -> gnome-panel

---

### Post by sept298901 on 2008-04-28
Thank you Sisco, that worked perfectly.

---

### Post by BWF89 on 2008-06-21
Thanks sisco311, I'm not a Linux newbie but I am an Xfce newbie.

---

### Post by Pipps on 2008-12-24
Thank you, Sisco!

---

