---
title: "Bumblebee (nVidia) problem on Wayland"
date: 2017-12-14
forum: General Help
---

### Post by stepheny on 2017-12-14
I am running Ubuntu 17.10 on Wayland on a laptop with nVidia Optimus. I have used Bumblebee to switch between the Intel and nVidia GPUs for many years, and many Ubuntu versions, now. Under Wayland, If I run a program with optirun for the first time in a session everything works fine, but if I close the program and try to run it again, or try to run any other program with optirun I get the following error message:
> $ optirun foobillardplus [ 449.381951] [ERROR]Could not connect to /var/run/bumblebee.socket! Error: Connection refused [ 449.382008] [ERROR]Could not connect to bumblebee daemon - is it running?
I tried stopping and restarting the bumblebeed and tried again. Then the error reads:

> [ERROR]Cannot access secondary GPU - error: [XORG] (EE) Failed to load module "mouse" (module does not exist, 0) [ 281.491449] [ERROR]Aborting because fallback start is disabled.
I also googled this warning and read that the package xserver-xorg-legacy could be the problem so I deleted that. But that didn't fix it either.

If I run Ubuntu 17.10 on Xorg I don't have this problem, I can close a program running via optirun and the start it again or run something else via optirun, as often as I like.

---

### Post by mastablasta on 2017-12-14
nvidia porprietary drivers are not fully supported by wayland. switch to xorg. problem solved. for now at least...

---

### Post by stepheny on 2017-12-14
Thanks, but I am not using nVidia prprietary drivers. I should have said that I am using nouveau.

---

### Post by mastablasta on 2017-12-15
those should work fine with wayland, however i am not sure how well bumblebee is supported.

in any case Wayland still seems like demo technology for now.

---

