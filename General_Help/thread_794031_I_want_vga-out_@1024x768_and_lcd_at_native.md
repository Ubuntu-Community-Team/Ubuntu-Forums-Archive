---
title: "I want vga-out @1024x768 and lcd at native"
date: 2008-05-14
forum: General Help
---

### Post by mfaust731 on 2008-05-14
Hey guys,
I have an asus eee 701 runnning 8.04
I have video out working, cloning the lcd display with the following command:

xrandr --outout VGA --mode 1024x768; xrandr --output LVDS --mode 800x480;;  #vga port 1024x768 , LCD 800x480

this does indeed set the vga port to 1024x768, but it also sets the LCD to the same - the LCD can only display 800x480

Im not sure if its a issue with my xorg.conf or my command

any ideas?

---

