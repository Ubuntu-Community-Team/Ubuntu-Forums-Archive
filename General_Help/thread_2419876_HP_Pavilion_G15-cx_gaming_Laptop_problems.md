---
title: "HP Pavilion G15-cx gaming Laptop problems"
date: 2019-05-26
forum: General Help
---

### Post by score100 on 2019-05-26
Hi people,
recently I acquired this laptop _HP Pavilion G15-cx0500nd _
 and I feel it's the most cursed machine for using linux I ever had do deal with.[B]

Things that weren't working out of the box (and now luckily do):
[/B]- Installation. In the end I had to use "nomodeset" to get the installer running
- Nvidia drivers. When installing the 390 drivers ubuntu wouldn't boot anymore using the latest kernel, with earliers it would. I found a solution adding "quiet splash nvidia-drm.modeset=1". This is something I copy-pasted from the web, no idea what it actually does but now it boots and the graphics card is recognized correctly. 
- When closing the laptop lid, the laptop would always go into airplane mode automatically. Some script hacking was neccesary.

[B]Things that weren't working out of the box and still don't
[/B]- sometimes my screen flips 90 degrees into vertical mode out of nowhere. Happened only once in ubuntu, second time while checking a livedisc of Pop_os. No idea also how to reproduce this.
- Action keys are only partially working. Volume keys are fine, but brightness keys don't work at all. Neither does airplane mode. 

Anyone else using this machine or one from the same series? Also any pointers to getting the latter problems fixed are much appreciated!
Cheers

---

