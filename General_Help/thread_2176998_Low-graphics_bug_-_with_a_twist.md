---
title: "Low-graphics bug - with a twist"
date: 2013-09-26
forum: General Help
---

### Post by Tha_Libster on 2013-09-26
After installing a recent set of updates with the update manager, my system now boots in low-graphics mode. This seems to be a [common bug]("http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error"); I've tried many of the solutions here to no avail. The real kicker is as follows:

When I try to log in, either through the GUI or through the shell opened with ctrl-alt-F1, I get a *login incorrect* error after typing in *just the username*. Furthermore, when I open a root shell through recovery mode, I can't change the password for the primary account - it gives me a *permission denied* error (and the filesystem is mounted to read/write). I fairly confident I'm using the correct username to attempt to log in, because when I
```
ls /home
```
there is only a single directory, and has this same username.

Potentially relevant information:
Ubuntu version: 12.04
GPU: NVIDIA 560 ti
gpu driver: Nouveau
CPU: AMD Phenom II X4 810

I am stumped. Any ideas?

---

### Post by Tha_Libster on 2013-09-28
Bump. I don't want to have to reinstall :(

---

### Post by tgalati4 on 2013-09-28
As a general rule, if you are running a proprietary graphics driver, it is directly hooked to the kernel.  The kernel is now called "tainted".  When you perform an update of the kernel (which you probably did) then you lose the proprietary driver--hence the low graphics mode.  So now you have to reinstall the proprietary graphics driver.  Normally this happens automatically (with a couple of reboots) and a pop-up of the Proprietary Hardware Detected dialog box.  So you can either reinstall the proprietary graphics drivers or bring up the Proprietary Hardware control panel and see what it says.

---

### Post by Tha_Libster on 2013-09-28
I'm pretty sure I was running nouveau, though. Since the problem arose, I've tried installing both nvidia-current and nvidia-current-updates and my system wouldn't even boot - it just ended up on a black screen with a flashing underscore. And the weird login errors are still confusing me :/

---

