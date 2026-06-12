---
title: "Keyboard config resets on reboot"
date: 2013-08-07
forum: General Help
---

### Post by pickarooney on 2013-08-07
Since updating to 12.4 my keyboard, which has always been EN-GB keeps resetting itself to EN-US whenever I restart. I have to run the keayboard configuration every single time, which is annoying as hell.
Does anyone have a reliable method (I've tried a few that simply don't work) of retaining my keyboard layout after rebooting?

---

### Post by pickarooney on 2013-09-30
I fixed this by adding
**setxkbmap gb**
to ~/.profile

---

