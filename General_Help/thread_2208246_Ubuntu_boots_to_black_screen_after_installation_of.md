---
title: "Ubuntu boots to black screen after installation of nvidia-331.49"
date: 2014-02-27
forum: General Help
---

### Post by Fabian_Ruhland on 2014-02-27
Hi,
Yesterday apt-get installed the new version of the proprietary nvidia-drivers (331.49) on my laptop which runs ubuntu 14.04 with kernel 3.13.5, and since then it just boots to a black screen. I can still access the consoles via Strg+F1, F2, F3, etc. I already tried to go back to nvidia-331.38, installing the kernel 3.13.0-12-generic (the one which originally comes with 14.04) and boot with FailsafeX, but all with no luck.
My laptop uses hybrid graphics with an integrated intel card, and an nVidia GeForce 760GTX, with bumblebee to switch between the cards. The modules nvidia-331/331.49 and bbswitch 0.8 are installed correctly via dkms, so I don't know why it is not working....

I hope anyone can help me.

---

