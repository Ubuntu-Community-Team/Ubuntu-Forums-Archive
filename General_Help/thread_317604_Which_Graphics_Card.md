---
title: "Which Graphics Card ?"
date: 2006-12-12
forum: General Help
---

### Post by Orbman on 2006-12-12
Hi,

I have a AMD 1800XP (1.53ghz) with 512mb ram, the graphics card i have in there at the moment is a ATI Radeon 9250 PCI 128Mb 64-Bit.

I have a spare Nvidia GeForce 2 MX400 64Mb AGPx4 card and was wondering which would give better performance, i dont play any really graphical games, the most i play at the moment is xmoto and UnrealTournamet (the first one).

At the moment xmoto is a bit choppy on the ATI, i know glxgears isnt a good way of measuring the FPS but it gives me 720ish.

Any guidence would be great. 

Thanks!

PS - I have tried both the opensource drivers and the ATI ones and didnt notice much difference.

---

### Post by xmastree on 2006-12-12
nvidia is better supported in linux, so I'd say give it a try. If anything, driver installation should be much easier.

---

### Post by kevinatkins on 2006-12-12
Hi,

The blessed ATI proprietary drivers can be a real pig to get working properly, even when installed using Synaptic or .deb packages. If you're not seeing much difference in performance between the open-source and proprietary drivers, then I'd hazard a guess that the proprietary driver isn't set up properly. Going from memory here.. open a terminal and type 'fglrxinfo' at the prompt - it should come back with a bunch of stuff clearly stating that the ATI 3D driver is functioning. If it says Mesa or anything else, the ATI driver ain't working properly and you're not getting 3D accelaration. In that case, google around and check the forums; if all else fails, bin the ATI and go with the nVidia card - the drivers are much nicer to set up!!

---

### Post by Orbman on 2006-12-13
Hey

Thanks for the input so far :)

i ran fglrxinfo and here's the output

> 
fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)


From that i assume they are running ?

Thanks.

---

