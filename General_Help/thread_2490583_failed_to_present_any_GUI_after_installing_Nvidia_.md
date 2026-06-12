---
title: "failed to present any GUI after installing Nvidia driver 535.104.05 (product branch)"
date: 2023-09-08
forum: General Help
---

### Post by ow1ty2 on 2023-09-08
computer configuration:
CPU: 13600kf
GPU: RTX4090
RAM: ddr4 64GB 3200MHz
OS: Ubuntu 22.04 LTS desktop


so I installed the nvidia driver by running the .run file downloaded from nvidia, then once I reboot, the screen only displays grey color (not black screen).

I blind-typed my password and it succedded, then automatically switched to tty2, GUI with no icons, instead of tty1 with the icons of disks, firefox, etc.

Lightdm is tried but it does not work, the icons are still hidden.

So what is the problem?

---

### Post by TheFu on 2023-09-08
Don't install drivers directly from vendors if your system is working.  This is especially true with GPU drivers.  Bad things happen often enough that it isn't worth it. Stick with drivers that have been tested by Canonical.

Use the Ubuntu built-in tools for this.
```
sudo sudo ubuntu-drivers autoinstall
```

Sorry, any other real help will need to come from nVidia, since they are using you as a pre-alpha tester on Linux.  They will ask for system logs, proof of which driver is being used, and which display manager you are running. Without that basic information, nobody can help.

---

