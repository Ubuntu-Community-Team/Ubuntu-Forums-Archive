---
title: "Additional Drivers won't install any driver"
date: 2017-10-15
forum: General Help
---

### Post by orthoducks on 2017-10-15
I installed a graphics card in a computer with a new installation of Ubuntu 16.04 and tried to install the appropriate driver for it with Additional Drivers. The application displayed the usual list of possible drivers. I chose one. It prompted me for my password. It worked for a few seconds, then reset the selection to the original driver (x.org X Server).

I tried the same card in another computer with Ubuntu 16.04. First, I used Additional Drivers with the computer's regular card to set the driver to x.org X Server. Then I installed the problem card and tried using Additional Drivers to change the driver. It worked perfectly, as it always has for me in the past.

The card is an NVIDIA 9800 GT. The driver was NVIDIA binary driver 340.102. However, I tried to use Additional Drivers on the first computer with several different models of NVIDIA cards and different driver versions, and I had the same problem with every one.

Does anyone know what would cause this? Does anyone know a solution, short of reinstalling Ubuntu and hoping for a better result?

---

### Post by Yellow Pasque on 2017-10-15
What kernel was each computer using? In other words, maybe do a fresh install of Ubuntu 16.04.1. It's possible the 340.xx driver doesn't work with the kernel/X of Ubuntu 16.04.3

---

### Post by Yellow Pasque on 2017-10-15
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/+bug/1677327](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/+bug/1677327)

---

### Post by orthoducks on 2017-10-16
The kernel version (from uname -r) is 4.8.0-36-generic.

That for both computers. They were installed from the same DVD.

---

### Post by Yellow Pasque on 2017-10-18
Okay, so what happens when you try to install the 340.xx driver in the terminal on the problematic system?

---

