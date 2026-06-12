---
title: "Stuck on purple screen (16.04) (Multiple reinstallations, same issue)"
date: 2016-08-07
forum: General Help
---

### Post by CaptainThrills on 2016-08-07
After installing 16.04 (on a samsung 850 250GB) a few days ago, fighting nvidia to work right, and then trying to make windows play nice, the installation seemed to completely fail, first with plymouth getting stuck in it's nice 5 dot loading sequence, after which it bumped into emergency mode, and glitched to hell, with input not being accepted, I restarted. At reboot, selected Ubuntu in grub, and then the infamous purple screen hang began, with no amount of restarts fixing it.

So like any other bug, I simply figured a reinstall was all I needed (and I lost my damn conky script). A few days go by, to today, and randomly on a reboot - plymouth stuck on 5 dot load, falls into emergency mode with no way to actually do anything, restart, and with recovery mode not working (*EXTREME glitches, I mean EXTREME* - wierd text bouncing, invalid input, nothing input properly, unable to do just about anything), I admit defeat. So turning to the internet to see if I have managed to put together the desktop from hell for Ubuntu.

(Yes I have tried boot-repair, but boot repair will not properly run with a GTX 1070 and nomodeset isn't doing squat, neither is removing the GPU).

Setup:
6700k (not OC)
msi z170-pro
evga gtx 1070 SC
DDR4/3000 (OC)
2x Samsung SSD 250GB
 1. Ubuntu UEFI
 2. WinBootMan UEFI
1x Samsung SSD 500GB

Have tried editing grub2 with nomodeset, nouveau.modeset=0, no splash quiet, etc. 
Any hope left or should I just fall into windows permanently? (2AM, been at this for 6 hours, probably burning out all my parts with 200+ restarts)

---

