---
title: "Strange error in fglrxinfo: DDX driver fingerprint mismatch"
date: 2007-03-01
forum: General Help
---

### Post by Munksgaard on 2007-03-01
Hi!

I have some problems with my graphics card. 
Im running Ubuntu 6.06 on a Toshiba Satellite M60-164, which has a 128mb ATI Mobility x600 graphics accelerator.
After having some trouble finding and installing the right drivers i now have this output from fglrxinfo which has some errors:

> ERROR: DDX driver fingerprint mismatch: got 0xC20D27F9, but expected 0x84220BA7
libGL error: InitDriver failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


I was hoping i could get some help finding and eliminating the source of the error with the driver fingerprint mismatch.

Any suggestions?
Thanks in advance
Philip Munksgaard

---

### Post by Maestro23 on 2007-03-01
Might want to try using the Envy script.

1. Download the correct drivers for your card.

2. Use the Envy script: [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

*Works for both ATI and Nvidia

Good luck.

---

