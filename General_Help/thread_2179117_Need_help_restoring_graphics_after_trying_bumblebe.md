---
title: "Need help restoring graphics after trying bumblebee"
date: 2013-10-06
forum: General Help
---

### Post by gamblor01 on 2013-10-06
I installed 13.04 on a Macbook Pro and it's mostly working.  I tried to setup bumblebee so I followed this tutorial:

[http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html](http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html)



Unfortunately I just got an error on reboot about being in low graphics mode.  I dropped into a shell and tried to troubleshoot but it all looks good.  Instead I tried to remove all packages I had installed and purge all nvidia-* packages.  No matter what I do, I can't seem to get the graphics driver working again.  It boots up and gives me the same error about low graphics mode and then just hangs there.  The mouse cursor never appears...I have to simply use CTRL+ALT+F1 to get to a console and that's all I can do.

So far I haven't been able to fix this with anything I have found on the interwebs.  Any ideas?

---

### Post by grahammechanical on 2013-10-06
Have you tried Recovery Mode>Resume. That should load without a proprietary graphics driver but with llvmpipe a sub-set of Nouveau. It is in the Advanced options. At working desktop you can experiment with video drivers. And then there is always a re-install. When I mess up and get bored or run out of ideas trying to fix it, I re-install.

Regards.

---

### Post by gamblor01 on 2013-10-06
I'm trying to avoid a complete reinstall.  I know it's not necessary!

I can't really get into recovery mode from grub.  I installed in a rEFInd environment and installed with ubiquity -b so the EFI boot loader is in use and not grub.  I can however drop to console with CTRL+ALT+F1 so I can run anything I need to from there to reconfigure the packages.  I tried dpkg-reconfigure on the intel driver but that didn't seem to work either.  :(

---

### Post by Yellow Pasque on 2013-10-06
These commands may help:
```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by gamblor01 on 2013-10-06
Still no luck.  :(

---

