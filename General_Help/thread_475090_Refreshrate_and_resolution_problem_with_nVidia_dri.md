---
title: "Refreshrate and resolution problem with nVidia drivers"
date: 2007-06-15
forum: General Help
---

### Post by Surkow on 2007-06-15
I installed Feisty and installed the latest nvidia drivers using envy. I have a dual head setup with a 21 inch crt monitor (capable of running at 85hz) and a 17 inch monitor (capable of running at 85hz). I want the resolutions to be respectively 1280x960 and 1024x768. I enabled twinview and after that I had to use "dpkg-reconfige -phigh xserver-org" to get from 320x480 to a normal resolution. I can use nvidia config panel to set the 17 inch monitor to use 1024x768 and 85hz. the other monitor however can' t go past 60hz (when I was still using the nv driver with even a higher resolution than 1280x960 could run with 75hz). I tried to alter the xorg.conf file horizontal and vertical refresh rate without success (I had to use dpkg-reconfige -phigh xserver-org again). When I check the ubuntu resolution manager it now only says 2304x960 which is not the currently used resolution (bug perhaps?). Can someone with knowlegde of this matter help me change the refreshrate of my 21 inch monitor to 85hz?

Specs:
- nVidia 7800GTX
- 17 inch crt monitor (Compaq v700) @1024*768
- 21 inch crt monitor (Compaq v1000) @1280*960
- nVidia Driver Version 100.14.09

---

### Post by Surkow on 2007-06-16
Bump

---

### Post by Surkow on 2007-06-16
I now understand that Ubuntu sees the two screen combined (that explains the resolution of 2304x960).

---

