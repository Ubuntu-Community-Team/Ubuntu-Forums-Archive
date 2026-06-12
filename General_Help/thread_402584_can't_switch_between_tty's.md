---
title: "can't switch between tty's"
date: 2007-04-05
forum: General Help
---

### Post by aidanr on 2007-04-05
hey, i just changed to a different keyboard with a different layout, so i searched and found this command to change the layout

sudo dpkg-reconfigure -plow console-setup

so i ran through that mostly just hitting enter and it changed the keyboard layout just fine, but i just realised that i can't switch between tty's anymore (ctrl+alt+[F1-F6])

anyone come across this before? any hints?

---

### Post by aidanr on 2007-04-08
for reference, i fixed this with a simple ```
sudo dpkg-reconfigure xserver-xorg
```
which i think i should've done in the first place :roll:

---

