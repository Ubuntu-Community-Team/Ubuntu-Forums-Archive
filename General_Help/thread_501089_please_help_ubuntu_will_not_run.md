---
title: "please help ubuntu will not run"
date: 2007-07-14
forum: General Help
---

### Post by punkrockermike21 on 2007-07-14
everything has been installed correctly and im sure of it because the ubuntu screen comes up with the orange loading bar. after the bar fills up and it should be loading the operating system at this point but my computer monitor says out of range meaning no signal. i think that this is because of my graphics card which is a geforce 6200 agp 8x card. someone help! ive seen my buddie use this operating system and its kickass.

---

### Post by merlinus on 2007-07-14
Press "Esc" at the grub boot menu, boot into recovery mode, login...then enter:

(or Ctrl-Alt-F1 to get to prompt)

sudo dpkg-reconfigure xserver-xorg

You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:

startx

or reboot...

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

-merlin

---

### Post by punkrockermike21 on 2007-07-14
ok when i do that it says that xserve-xorg is not installed. now what do i do. and thank you for the help, i'm love n all this free help

---

### Post by merlinus on 2007-07-14
> **punkrockermike21 said:**
> ok when i do that it says that **xserve-xorg** is not installed. now what do i do. and thank you for the help, i'm love n all this free help

Should be

** xserver-xorg**

It's often best to copy-and-paste -- easy to miss a letter or number.

:)

-merlin

---

### Post by punkrockermike21 on 2007-07-14
thanks i'm an idiot

---

