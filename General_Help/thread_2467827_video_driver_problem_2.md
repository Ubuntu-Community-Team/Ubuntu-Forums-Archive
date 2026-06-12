---
title: "video driver problem 2"
date: 2021-10-08
forum: General Help
---

### Post by jgw on 2021-10-08
I have now changed my display card.  I was using a geforce 8600gt 512mb ddr2  and I updated to an XFX NVIDIA GeForce 9500 GT Video Graphics Card 1GB DDR2 PCI-e VGA DVI S-Video  

My problem is that my display sometimes goes amuk.  It was worse on the old one which I changed from the x org x server to nvidia-340.  The installation of the nvidia 340 was a disaster and I went back to open source driver and I still had problems.  Then I updated my display card to the geforce 9500 GT card which had a full 1gb of memory.  Updating to a better card with more memory, I thought, was fix the problem.  I am currently running that card with the open source driver which was the one the system decided to use with the new card.  

My display will, sometimes, go bezerk and start flashing stuff (just stuff, lines, block, black and white stuff, etc).  It doesn't happen all the time and seems to like to do it if I have two things on the display and one is smaller than the other and then they do visible battle.

I have no idea what I might do to fix it.  I don't trust nvidia 340 given my last attempt.  

I can live with the screen going crazy sometimes but it would be nice to have it stopped.

Thoughts?

---

### Post by aug7744 on 2021-10-08
Your machine has enable integrated video in mainboard ? try disable.
Try disable in Nvidia settings the option flipping in OpenGL settings and also disable dithering in monitor settings.

---

### Post by jgw on 2021-10-09
Thank you for the reply!

I started to turn off my machine to get to the bios and then decided to remove my nvidia display card and go with the integrated video instead.  I have no idea why I even did the card thing but I have been testing the built in video and it does everything I need.  So I am now using:
Display
Resolution:               1920x1080 pixels
OpenGL Renderer:	AMD RS780 (DRM 2.50.0 / 5.11.0-37-generic, LLVM 12.0.0)
X11 Vendor:	        The X.Org Foundation
 
It seems to be running just fine!   I am going to mark this as solved - Thanks again!

---

