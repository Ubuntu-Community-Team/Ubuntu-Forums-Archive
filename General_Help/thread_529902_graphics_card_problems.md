---
title: "graphics card problems"
date: 2007-08-19
forum: General Help
---

### Post by patmalcolm91 on 2007-08-19
hello, i am currently running ubuntu feisty on my dell inspiron 630m laptop. so far the only thing making me keep a windows computer in the house is that i need to run Sketchup. I've tried programs like K-3D and Wings3D, but in both of these, i get a very glitchy display area, most of the time it's black until i drag the window, then it will blink the image and go back to black. I've also tried sketchup under wine. From most of the reports on wine's website, it should work, but i get a black drawing area, and about 1 out of 5 times it will eventually properly display for a few minutes.

I've come to the conclusion that my graphics card is probably to blame. lspci gives this as my graphics card:

VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller

is there a better driver or a fix for this??? If i could run sketchup under linux, i can completely switch over. thank you in advance for any help.

---

### Post by FinMedBart on 2007-08-20
Just fixed this on my LG LW40 express with the same intel chipset (915GM).

The strange thing that made this work for me was to:

1. create a new user

2. installing the intel driver for xserver

            sudo apt-get install xserver-xorg-video-intel

and hitting alt+ctrl+backspace to restart gnome.

The funny thing, or the bug, is that if I try to log on with my original user name xserver just won`t start. The screen blinks, go black and i loop back to the log on screen. But when I use my  newly created account everything works. :confused:
But I can`t choose 1280x800 in the screen resolution settings. I`am stuck with 1280x768

---

