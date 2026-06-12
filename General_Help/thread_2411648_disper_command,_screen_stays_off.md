---
title: "disper command, screen stays off"
date: 2019-02-01
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2019-02-01
For my mom's setup i mad a script to switch the display from one room to the other room
[FONT=courier new]disper -s[/FONT] for one room and [FONT=courier new]disper -S[/FONT] for the other room, i upgraded the tiny 1600x900 (dvi -dvi) display to a 1920x1200 (dvi -> hdmi) display, but i has to revert cause i can ot figure out how to get the disper command to work right
if i change it manually via nvida-setting it works fine
i tried manually inputting the resolution, but it did not work aside from using -r 1920x1200 what else can i define?

---

### Post by pqwoerituytrueiwoq on 2019-02-03
did some more fiddling with it today
[FONT=courier new]disper -s[/FONT] and [FONT=courier new]disper -s -r 1920x1200[/FONT] result in no display, oddly [FONT=courier new]disper -s -r 1920x1080[/FONT] works but 1920x1200 is the native resolution for this display
i was able to get it with xrandr
[FONT=courier new]xrandr -d :0 --output HDMI-0 --off --output DVI-I-1 --auto[/FONT]

---

