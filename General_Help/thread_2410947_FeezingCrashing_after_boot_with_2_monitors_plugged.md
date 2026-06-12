---
title: "Feezing/Crashing after boot with 2 monitors plugged in"
date: 2019-01-22
forum: General Help
---

### Post by frankenfish on 2019-01-22
I've been experiencing freezing/crashing several seconds after boot when I have both of my monitors connected. Sometimes it happens before login, sometimes i can get to the desktop, but it always happens. the screen will lock up and eventually go black. setting it to only use 1 monitor doesnt help it needs to be physically disconnected. but with only 1 connected everything works perfectly. ive tried ubuntu, kubuntu, and i have xubuntu installed right now they all do the same thing.

My specs:

Xubuntu 18.10
Mobo: AsRock b85pro4
CPU: i5-4460
RAM: 8gb
GPU: R9 390 (1x 3840x2160 connected to DisplayPort, 1x 1920x1080 connected to HDMI)
1x SSD 
2x 1TB HDD 
1x 600gb HDD

Xubuntu is installed on a partition of one of the 1tb drives

---

### Post by him610 on 2019-01-22
Welcome to the forums frankenfish. May we see, between the code tags, the results of...
```
inxi -F
lshw -c display
xrandr
```

---

### Post by frankenfish on 2019-01-23
after much googling and hair pulling and head desk slamming it seems the problem is with my 390 itself. this seems like a fairly common problem for amd gpu's and there doesnt look like there's any easy quick fix for it. i was able to get as far as blacklisting the radeon driver to force it to use amdgpu and that causes it to hang on the purple loading screen. i was able to login once by going to recovery mode and then booting normally but that only worked once

---

