---
title: "Switch grub display out"
date: 2022-04-26
forum: General Help
---

### Post by chaython on 2022-04-26
By default, grub is displaying on the wrong monitor, ubuntu login screen also appears on the audio reciever not the display set as primary... Ontop of this the audio device keeps resetting to line in rather than the HDMI audio device.Display out: Nvidia RTX 3080 w/ 1hdmi to Pioneer audio reciever, 1 dp to Samsung monitor, 1 dp to benq monitor.Samsung 4k  flickers when the resolution is too low [such as by grub, and doesn't display out]Poneer reciever is used for speakers no display outSo I need to assign it to my benq monitor....By default Manjaro was set to my benq moniitor and had a nice gui for grub....But ubuntu sadly is not, I switched back to ubuntu because I wanted secure boot so I could play valorant in windows 11.

---

### Post by chaython on 2022-04-26
How do I add line breaks in this forum?

---

### Post by QIII on 2022-04-26
Line breaks should be added as you would normally expect them to be.

Some oddities may occur if using WYSIWYG mode.  Try toggling the button I have highlighted in blue in this image:

[ATTACH=CONFIG]290346[/ATTACH]

---

### Post by chaython on 2022-04-26
It's because I am using a browser without javascript. But even br command is ignored. Dumb. Anyways the solution is adding "GRUB_CMDLINE_LINUX="video=HDMI-0:d video=DP-0:e"

---

