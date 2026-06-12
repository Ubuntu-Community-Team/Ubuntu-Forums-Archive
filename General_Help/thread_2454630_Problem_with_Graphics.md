---
title: "Problem with Graphics"
date: 2020-12-03
forum: General Help
---

### Post by nilszan on 2020-12-03
Hi

I'm new to Linux and Ubuntu and need help to solve an encountered problem.

Recently I bought a new computer with the GeForce GTX 1660 SUPER  graphics card installed. As it is was my intention to use this comptuer  for machine learning I tried to install the CUDA toolkit 11.1 from  developer.nvidia.com/cuda-download after having installed first Ubuntu  20.04.   

Unfortunately the installation failed and terminated at 88 % complete.

 When I tried restarting the computer after this the graphics seem to  have gotten messed up and even after erasing the disk and re-installing  the OS the problem remains. There must have been something which changed  on a level outside of the OS therefore I imagine. Now there is only a  primitive gnu grub text interface being displayed. However it is  possible to run the device in "Try Ubuntu" mode with a USB plugged in.  There I can install Ubuntu again and it can be run until restart which triggers the same gnu grub interface.

I'm wondering if it is possible to use either the BIOS, 'Try Ubuntu' mode or a flash drive in order to restore or change the graphics card / drivers to some other state?

Thanks!

---

### Post by CelticWarrior on 2020-12-03
Welcome.

First of all there's no reason for when installing the second time, doing the same as before, and obtain different results. There must be something you're doing differently.

Let's start with the obvious: Disable Secure Boot in UEFI.
Then reinstall Ubuntu 20.04 making sure to select installation of drivers, codecs, etc. This should install the correct Nvidia driver. Then install Cuda from the Ubuntu repositories as well, not from the Nvidia binary.

---

### Post by nilszan on 2020-12-03
Yes, now after following the steps you mentioned it worked out and the Cuda installation was successful as well with the Ubuntu repositories. Thanks!

---

### Post by CelticWarrior on 2020-12-03
You're welcome.

Please use the thread tools to select solved. It helps future readers.

---

