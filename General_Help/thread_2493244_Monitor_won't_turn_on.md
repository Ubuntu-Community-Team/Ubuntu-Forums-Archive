---
title: "Monitor won't turn on"
date: 2023-12-07
forum: General Help
---

### Post by lovelychaoticcupcake on 2023-12-07
This has been a journey, i'm still new to Ubuntu and don't really know what i'm doing.
 I updated Ubuntu and it kept getting stuck on the boot screen and would say 'recovering journal', so i tried fsck and kept getting an error for /dev/nvme0n1p2 is mounted and couldn't run.
now the PC turns on but the monitor doesn't, i tried taking out the video card and just using the onboard graphics but nothing is working. i also tried a tv and another monitor.
i cant see anything to check, am i screwed?

---

### Post by TheFu on 2023-12-09
Try booting off the Ubuntu Install flash drive and going into "Try Ubuntu" mode. It that doesn't work, it is most likely a cable or monitor issue.
If it does work, you've isolated the problem to be within the installed OS settings and/or perhaps the storage subsystem.

In troubleshooting, it is all about simplifying the situation and testing.  Repeat the simplification and testing over and over, until you've isolated the smallest group of parts to determine the issue.

You've done some of it by trying different monitors and the different GPU.  But if you didn't try a different cable, that $6 item could be the entire problem.  Trying the "Try Ubuntu" mode from any Ubuntu Install ISO is the next thing to try - with the old cable.

---

### Post by MAFoElffen on 2023-12-09
Just an idea...

If an older motherboard, for the iGPU on the motherboard, sometimes there was either a set of pins on the motherboard or a setting on the BIOS to tell it which GPU to use as the primary display...

If newer, then some have a setting in BIOS, and some don't.

---

