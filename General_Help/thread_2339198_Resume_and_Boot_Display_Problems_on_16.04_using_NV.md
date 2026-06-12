---
title: "Resume and Boot Display Problems on 16.04 using NVIDIA Card on Dell Inspiron"
date: 2016-10-05
forum: General Help
---

### Post by gpone2 on 2016-10-05
Hey all,

I installed Ubuntu 16.04 Desktop alongside Windows 10 Home on a Dell Inspiron 15-7559 with an Nvidia 960m card and embeded Intel Skylake graphics.

When I first installed Ubuntu and attempted to boot, the display would freeze on the Ubuntu splash screen after entering my disk password. Strangely, by removing "quiet" and "splash" from my grub configuration during my next boot, I was able to finally boot to the login screen and access the desktop. I installed the Intel and Nvidia drivers in the "Additional Drivers" app and now I can boot to the login screen with no issues.

Now, when closing the laptop lid to suspend the system, it resumes to a blank screen and I can't get it to recover from this state without holding the power button to force shutdown. I verified that it is a display issue because I was able to ssh into the machine while it had the blank screen.

I was able to install and boot into the latest (4.8) mainline kernel, which also gave me a warning/error because of my installed proprietary drivers. I tried uninstalling the Nvidia drivers to see if Nouveau had been fixed/improved, but the previous splash screen freeze returned; I was able to reinstall the drivers by booting into 4.8 recovery mode and using the Failsafe graphics mode to reinstall the Nvidia drivers.

Any help on getting Nouveau to work nicely with the 960m so I don't have to run proprietary drivers or solve the suspend issue?

---

