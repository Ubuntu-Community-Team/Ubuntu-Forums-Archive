---
title: "can not write to DVD 16.10"
date: 2016-11-24
forum: General Help
---

### Post by badger-badgerclan on 2016-11-24
Right click on iso file brings up 'Open With Disk Image Writer'. In the 'Restore Disk Image' box click on Destination and the cd/dvd player is listed but not active. Did a fresh install of 16.10 on both a PC and laptop and both have this problem. Tried installing Brasero and get the following:
The following packages have unmet dependencies:
 brasero : Depends: libbrasero-media3-1 (= 3.12.1-1ubuntu5) but it is not going to be installed
           Recommends: brasero-cdrkit but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by g33zr on 2016-11-24
Try burning the iso with xfburn instead. To install: sudo apt install xfburn

---

### Post by badger-badgerclan on 2016-11-29
After trying various ways to fix the broken packages problem without success, replaced the problem sources.lists with my sources.lists.bak file and the broken package problem was fixed. Then installed Brasero without any problem and was able to burn the iso to DVD. Burning a new DVD after a fresh install should NEVER be a problem,:(

---

