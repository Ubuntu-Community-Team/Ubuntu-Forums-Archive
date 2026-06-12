---
title: "Wine through LTSP"
date: 2007-09-14
forum: General Help
---

### Post by MLAdk on 2007-09-14
I have set up a server with LTSP5 and installed IEs4linux and when running locally on the server Wine and "Internet Explorer" (IE) works fine.
But when connected to the server with a thin client it does not work. When starting IE (or winecfg) I get a black screen and then a new ubuntu login screen.
I figure the problem most be related to the settings of X, LTSP, or wine. And I have searched google but cant find any info on what could cause this problem or how to solve it.

Specs.:
Server:
Quad core Xeon, 4 GB RAM, 2x 1 Gb network, SATA300 disks in RAID1
Clients:
1GHz VIA C3, 128 MB RAM, onboard Intel graphics, 100 Mb network
LAN:
1Gb switch and the server is running dhcp.

I'm using Ubuntu at the moment but plan to change to Edubuntu or Xubuntu.

Any help on how to get Wine/IE to run when connected with a client is appreciated.

Thanks in advance.

---

### Post by MLAdk on 2007-09-15
I Know of two possible solutions:
1) Make wine and ies4linux a plugin on ltsp-build-client. How do I do that?
2) Make wine settings (maybe Xorg or LTSP settings) so that the client will not crash when running wine (or a program through wine). I have tried to change some settings, but that did not change anything. Maybe I just have not found the right place to make configuration of wine with respect to how it works with X11.

Any help or ideas would be appreciated, since I have run out of solutions myself.

---

### Post by MLAdk on 2007-09-17
The easiest solution is to use crossover instead of just wine. Then it will work with no problems at all.
I have decided that further investigation is a waist of time.

Have fun,

---

