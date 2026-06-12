---
title: "GRUB shows several kernels, help!"
date: 2008-07-01
forum: General Help
---

### Post by Master_Z on 2008-07-01
Any reason my GRUB bootloader shows kernels:
-2.6.24
-2.6.24-18
-2.6.24-16-386
-2.6.24-16

They just randomly appeared. I had tried installing another kernel so that Virtualbox would run, but I guess I screwed it up. I need them uninstalled, but I want the original there (2.6.24-18 ). Thanks.

---

### Post by soccerboy on 2008-07-01
you can actually leave them there, they won't do any harm.  You can change your default boot kernel by editing /boot/grub/menu.lst or by using something like startupmanager.

---

### Post by logos34 on 2008-07-01
Open Synaptic and search for:
[B]
linux-image-2[/B]

This will list all the kernels. Delete all of them except the -18 pkg.

Then run 

**sudo update-grub** 

to clean up menu.lst

---

