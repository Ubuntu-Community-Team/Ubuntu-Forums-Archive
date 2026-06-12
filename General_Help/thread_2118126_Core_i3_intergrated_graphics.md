---
title: "Core i3 intergrated graphics"
date: 2013-02-20
forum: General Help
---

### Post by Spae on 2013-02-20
I have a sandybridge laptop, cpu has integrated graphics but ubuntu is not using it. How can I install a graphics driver (+ opengl) on ubuntu 12 for the core i3? (Game i play is forced into cpu/software rendering mode when it has opengl support, as such my laptop is getting super hot)

---

### Post by dino99 on 2013-02-20
from synaptic, you already should have xserver-xorg-video-intel installed.

is that laptop also have a dedicated video card , on which you should ask to work with? if so, which one it is ?

note: inside synaptic, check the latest tab to know which video driver is activated.

note2: check the graphic bios settings (some have choice to select a card or the chipset)

---

### Post by Spae on 2013-02-20
Oh, for some reason ati drivers were installed as well. I only have integrated graphics not dedicated. Un-installed ati from synaptic, fixed. thanks

---

