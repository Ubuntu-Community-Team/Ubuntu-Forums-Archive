---
title: "live to normal install"
date: 2005-06-07
forum: General Help
---

### Post by CoMaNdore on 2005-06-07
Hi all


Im almost a complete n00b on nix, I managed to get ubuntu working on
my school comp, and the home one ( dual boot on both of them )

Now I wanted to install ubuntu on my laptop. Okay I put in the ubuntu install 
disk, and waits. I get to press the [ENTER] key and it starts to install, after a little time with some init going on (text on screen and stuff) the screen just fade to
white.. and there it is stuck.

oh no I thought, so  I tried the Ubuntu Live cd ( got it at The Gathering 05 :D )
And it works like a charm.. I can get into and gnome works perferct.


So what I want to do is to install ubuntu from the live cd...
As the ubuntu install disk dont seem to work for the laptop. 

How can I do this ?
apt-get install the-whole-damn-thing ?

( info: i got a desent internet line so dl everything from the net is a option if somebody tells me how to do this... )

---

### Post by Martin Witte on 2005-06-07
try to boot with option vga=771, that is the setting for laptops

---

### Post by CoMaNdore on 2005-06-07
that did the tick !

thank you a LOT !

---

### Post by SNo0py on 2005-06-08
No, you can't install from the live CD. But you can try to add some parameters to the install-CD at the booting prompt. For example I had to disable the framebuffer before I was able to install Ubuntu.

---

