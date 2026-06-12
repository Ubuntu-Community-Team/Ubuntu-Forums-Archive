---
title: "DVD playing lockup"
date: 2007-04-05
forum: General Help
---

### Post by marco999 on 2007-04-05
Hello,

I was playing a dvd with my install of Feisty (patched to most recent updates), with the latest nvidia drivers installed for my 8800GTS. About a quarter way through the movie the computer froze and kept repeating the same sound of the current scene. It also started flashing the Caps lock and Scroll lock keys. The only way that I could fix this was to reboot.

By the way 3D acceleration was enabled with the latest Restricted Modules.
What the heck caused this?


My system specs are:
P4 3.2Ghz
P5N-E SLI
1 GB DDR2 PC6400 800 mhz OCZ Ram.
Sound blaster Live 5.1(SBO102)
Plextor DVD Burner model PX-755SA (I was using this to play the DVD)
Toshiba DVD-Rom
EVGA 8800 GTS 640 MB


Please help me with this I really want to play DVDs with Wubi and Feisty.

Marco999

---

### Post by marco999 on 2007-04-05
Still no reply. Well I have installed an updated kernel; for the Kernel I have these packages installed:

linux-headers-2.6.20-12
linux-headers-2.6.20-12-generic
linux-headers-2.6.20-13
linux-headers-2.6.20-13-generic
linux-headers-2.6.20-14
linux-headers-2.6.20-14-generic
linux-headers-generic                    Version 2.6.20.14.12
linux-image-2.6.20-12-generic
linux-image-2.6.20-13-386
linux-image-2.6.20-13-generic
linux-image-2.6.20-14-generic   Version 2.6.20-14.22
linux-image-generic                      Version 2.6.20.14.12

As well as the restricted modules for the Nvidia Driver.

These are the packages that I have installed for the Kernel. Please someone help me solve this.

and If not please someone help me find where the logs are atleast.

P.S I have already defragged my hard drive that Ubuntu is installed on. This made no difference.


Marco999

---

### Post by ago on 2007-04-06
Hi there, 

this looks more like a generic Ubuntu problem. Anyway you cannot really change the kernel at the moment, but you can install restricted-modules and ant drive you want for the kernel version 2.6.20-12-generic. All the linux logs are in /var/log.

---

### Post by marco999 on 2007-04-06
So this is a generic kernel issue? Or is it a Feisty bug?

All I really want to know is - Is there a way to fix this?

What do you mean I cahnge change the kernel? I installed an updated one via the update-manager.
This didn't fix the pbolem.

marco999

---

### Post by ago on 2007-04-06
The latest minefield (12) released today should be able to upgrade the kernel. Not sure if that is going to help with dvds though

---

