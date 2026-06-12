---
title: "Envision LCD Moniter - Input not supported error"
date: 2007-11-05
forum: General Help
---

### Post by grimdaze on 2007-11-05
I decided to install Ubuntu through Wubi and all went well with the install.
But upon trying to boot into Ubuntu before any loading begins my Envision LCD monitor goes black and a gray box that says "Input Not Supported" starts bouncing around the screen.

I looked it up on the Envision site and found
> 
Q  	Monitor displays “Input Not Supported”. (LCD monitor only)
A 	This means the computer is sending an incompatible display mode to your monitor. Please check the user’s manual for supported display mode or input and configure your computer to those settings. The recommended setting for LCD panel is 1024x768 resolution and you may need to change the refresh rate of the monitor to 60Hz. Click here to go to Safe Mode procedure.


Any ideas how to fix this?

---

### Post by ago on 2007-11-05
You may need to select a lower resolution

alt+f2
sudo dpkg-reconfigure xserver-xorg

---

### Post by grimdaze on 2007-11-05
Edit: Nvm, it worked the second time around. Thanks.

---

