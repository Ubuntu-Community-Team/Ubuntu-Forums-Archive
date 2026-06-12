---
title: "GRUB Wait Time"
date: 2006-12-14
forum: General Help
---

### Post by BlahMan_of.Doom on 2006-12-14
Hi there, I'm new to this forum, but anyways here goes:

How do I edit the default wait time in GRUB? The default is ten seconds, but I want to make it 30. Thanks!

---

### Post by hardyn on 2006-12-14
if you open menu.lst in your editor...

sudo gedit /boot/GRUB/menu.lst (i may have the character case incorrect)

its a VERY well documented file, there will be an entry just to change the wait time, change it to an integer value of your choice.

(im at school right now and not in front of my ubuntu machine, i appologize for the poor post, hope it helps anyway)

---

### Post by Azakus on 2006-12-14
The settings is called "timeout".  It's near the top of the grub file. Change it to whatever you want.

---

### Post by BlahMan_of.Doom on 2006-12-15
Thanks :)

---

