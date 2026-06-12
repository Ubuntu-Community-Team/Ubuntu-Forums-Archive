---
title: "Ubuntu loads up but shows black screen after some hardware upgrades"
date: 2008-06-20
forum: General Help
---

### Post by DMBoricua on 2008-06-20
I recently did an upgrade to my desktop tower on video card and RAM. Previously I had a GeForce 6800 GS AGP card, and 1GB of DDR RAM (two 512MB sticks). 

Now I've got an HIS Digital ATI HD Radeon 3850 512MB GDDR3 AGP, and got two 1GB sticks of RAM to have 2GBs of RAM on my system.

My tower has 3 hard disks, each with an OS. I got XP, Vista, and Ubuntu. I've first done my part on installing the proper drivers on XP and Vista (I havent got the drivers to actually work on Vista but I'll soon find a working one, hopefully). Next it was Ubuntu. :)

I booted up Ubuntu fine, with a very low resolution as expected from installing a new card. Soon came a popup on my desktop screen saying it found the available driver to be enabled for my ATI. Clicked enabled, being aware that it will have no support whatsoever, and did a reboot. Then I would see the logo of Ubuntu loading up, but when its done the screen just goes black, and there is no hard disk activity. What could be the problem?:confused:

---

### Post by dracayr on 2008-06-20
hi,

what about the linux kernel magic key sequence:

SysReq(that's normally alt+printScreen) + r + e + i + s + u + b
(of course you don't have to press those keys simultanously, but they should be only seconds apart (the faster the better)). That should restart the system. If not, it means that the kernel crashed, which is VERY BAD. Did you try the recovery mode?

dracayr

---

### Post by DMBoricua on 2008-06-20
Yeah forgot to mention, I have done recovery mode but it does the same thing, when the selection screen comes up (the one with 3 options, resume booting up, drop to prompt, and fix x server) I choose resume but a few lines down and the screen goes black again.

I just tried that SysReq alt+print screen + r + e + i + s + u + b and nothing happens :confused:

---

### Post by dracayr on 2008-06-20
what about "drop to prompt"? If that works, try "fix the x server".

dracayr

---

### Post by avtolle on 2008-06-20
> **dracayr said:**
> what about "drop to prompt"? If that works, try "fix the x server".

dracayr
I would first try "fix the x server" first.

---

### Post by DMBoricua on 2008-06-20
Hehe there we go, I selected fix x server and resumed booting and I could go in now :) thanks, I never thought that fix x server would fix bootup, I thought it was to fix something related to network or whatever :p

Now my prob is my screen resolution wont go higher than 1280x1024. When I had version 7.10 I used to have an application that I could specify what brand monitor I have, what model and if its widescreen or normal, but I dont seem to find that anymore on 8.04. I have a 22 inch widescreen LCD and would want 1680x1050 resolution, how can that be done?:confused:

---

