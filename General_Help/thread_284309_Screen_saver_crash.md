---
title: "Screen saver crash"
date: 2006-10-25
forum: General Help
---

### Post by laurenx on 2006-10-25
I have just installed Ubuntu on a new desktop. My machine regularly freezes after a few minutes when the screen saver kicks in. I have 1 gig of RAM and nothing else running. I feel like I am back with Windows 98! Anyone know what the problem is, I so want Ubuntu to be a realistic option to Monopolysoft!

---

### Post by madmetal on 2006-10-25
which vga card do you have and do you have the driver installed?
you may use a 3d screensaver and this may create problem.

---

### Post by laurenx on 2006-10-25
I have an nVidia GeForce 7300LE 3D PCI-Expres card, and yes the screen savers are in 3D. I thought they looked very nice...does this mean I have to get rid of them? If so, what do I do?

Lauren

---

### Post by madmetal on 2006-10-25
have you nvidia driver installed?

---

### Post by laurenx on 2006-10-25
No..do I need one? If so, what should I do?

Also, (now this is probably a stupid question) but if the problem is I don't have the right driver for my graphics card, how come the graphics work at all?

Lauren

---

### Post by madmetal on 2006-10-25
open a terminal and run 
glxinfo | grep direct
this shows if you have 3d acceleration on..
if answer is no then 3d screensaver wont work properly..
drivers make the card work at its max and is used mainly for 3d.
to install nvidia driver open synaptic and search for nvidia driver or look forum for a better how-to..

---

### Post by laurenx on 2006-10-25
Thanks Madmetal, this gives me something to work on.

Laurence:-k

---

### Post by madmetal on 2006-10-25
anytime! ;) 8-) 
inform us if you fix it!

---

### Post by laurenx on 2006-10-26
Well, I used easy Ubuntu to install the nVidia driver, but the problem has got worse. Now the computer freezes immediately the screen saver starts; I can't even turn off the screen saver because the turn off screen shows a sample of the screen saver, causing the machine to crash immediately!

The program "sysinfo" shows that the graphics chip is GeForce 7300 LE and the 3D accelerator driver is NVIDIA Linux x86 Kernal Module. I have an AMD 3800 processor.

I don't really understand terminal commands, but if I type glxinfo as suggested yesterday it says: 

xlib: extension "GLX" missing on display "0.0". (this line several times)
Error couldn't find RGB GLX visual"

and then there is some more stuff about Qx21 tc etc etc.

Does this mean the driver is installed but the acclerator is not on? Is so, what can I do to turn it on?

Laurenx](*,)

---

