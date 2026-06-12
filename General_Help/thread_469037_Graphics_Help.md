---
title: "Graphics Help"
date: 2007-06-09
forum: General Help
---

### Post by Infinia on 2007-06-09
[I]First of all I want to tell the problem that occurred when trying to install ubuntu.
When choosing the country with the Magnifying glass on the Live CD, clicking anywhere on the map would cause the computer to "freeze up" . Sometimes I could move the mouse & sometimes I couldn't. (But I chose the county with the large list provided)[/I]

Now ubuntu is installed. I love it!
But when I have my restricted drivers on, the computer will 'randomly' restart or freeze up.
But without the drivers on my Cedega doesn't run Stacraft! We'll, it does in a way but the game looks all stretched and stuff. But when I take a screen shot, IT LOOKS PERFECTLY FINE IN THE SCREENSHOT! WTF!!!

So my brother told me it would be a good idea to post about my problems on this forum and also that its for sure the Video Card's problem.  Also my ZSNES works perfectly fine when I'm not it full screen that is, because when I am it looks like Starcraft does XD.

I did the **sudo gedit /etc/X11/xorg.conf ** and under my Section "Device" it says 
Section "Device"
Identifier "Generic Video Card"
Driver "vesa"
BusID "PCI:1:0:0"
EndSection

I changed the Driver from **vesa** to **ATI** and now I need to know what else I should put...

infinia

---

### Post by Copperteeth on 2007-06-09
no idea sry

---

### Post by orb9220 on 2007-06-09
You need to post what your video chipset is. And you need to install the one for it.

I have nvidia so I installed the nvidia drivers for it.

---

### Post by orb9220 on 2007-06-10
And I answered your private and sent link to all threads on Radeon 9550
[http://ubuntuforums.org/search.php?searchid=21797884](http://ubuntuforums.org/search.php?searchid=21797884)

---

