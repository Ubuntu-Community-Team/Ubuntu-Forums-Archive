---
title: "Screen resolution 2560x1440 unavailable"
date: 2018-07-31
forum: General Help
---

### Post by satimis on 2018-07-31
Hi all,

Ubuntu 16.04.4

&#10219; cat /var/log/Xorg.0.log | grep 2560x1440```

[    10.531] (II) NOUVEAU(0): Modeline "2560x1440"x0.0  241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync (88.8 kHz eP)
[    11.027] (II) NOUVEAU(0): Modeline "2560x1440"x0.0  241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync (88.8 kHz eP)
[    16.774] (II) NOUVEAU(0): Modeline "2560x1440"x0.0  241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync (88.8 kHz eP)
[    17.095] (II) NOUVEAU(0): Modeline "2560x1440"x0.0  241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync (88.8 kHz eP)
[    17.279] (II) NOUVEAU(0): Modeline "2560x1440"x0.0  241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync (88.8 kHz eP)
[    18.294] (II) NOUVEAU(0): Modeline "2560x1440"x0.0  241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync (88.8 kHz eP)
[    54.685] (II) NOUVEAU(0): Modeline "2560x1440"x0.0  241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync (88.8 kHz eP)
[    57.350] (II) NOUVEAU(0): Modeline "2560x1440"x0.0  241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync (88.8 kHz eP)
[   204.182] (II) NOUVEAU(0): Modeline "2560x1440"x0.0  241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync (88.8 kHz eP)

```

&#10219; cat /var/log/Xorg.0.log > xorg.0.log.txt
Please see file xorg.0.log.txt attached

Please help.  Tks

Sorry unable to attach the file here, exceeding file size limit

Regards
satimis

---

### Post by Autodave on 2018-07-31
What video card are you using? Have you tried going to Settings -> Additional Drivers to see if there is a driver available?

---

### Post by satimis on 2018-07-31
> **Autodave said:**
> What video card are you using? Have you tried going to Settings -> Additional Drivers to see if there is a driver available?
Hi,

I couldn't find 'Setting'
Only 'System Settings' and 'Onboard Settings'

&#10219; lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:        16.04
Codename:       xenial

```

Do I need to install 'unity-tweak-tool' ?

This is a new 2TB SSD just having Ubuntu 16.04.4 installed.

I have an old 1TB SSD on this PC running Ubuntu 16.04.  I can find screen resolution 2560x1440

Edit-1
====
&#10219; sudo lspci|grep VGA
[sudo] password for satimis: ```

01:00.0 VGA compatible controller: NVIDIA Corporation GK208 [GeForce GT 730] (rev a1)

```


Edit-2
=====
Do I need to install 'Proprietary Nvidia GPU Drivers' as mentioned on document below; ?

Install Proprietary Nvidia GPU Drivers On Ubuntu 16.04 / 17.10 / 18.04
[https://websiteforstudents.com/install-proprietary-nvidia-gpu-drivers-on-ubuntu-16-04-17-10-18-04/](https://websiteforstudents.com/install-proprietary-nvidia-gpu-drivers-on-ubuntu-16-04-17-10-18-04/)


Regards
satimis

---

### Post by Autodave on 2018-07-31
You need one (either) of the 390 drivers. I am not using Ubuntu, but try System Settings -> Additional Drivers.  Alternately, the repositories (synaptic) has the driver you need: you can get it from there.

---

### Post by satimis on 2018-07-31
> **Autodave said:**
> You need one (either) of the 390 drivers. I am not using Ubuntu, but try System Settings -> Additional Drivers.  Alternately, the repositories (synaptic) has the driver you need: you can get it from there.
Hi,

Problem solved as follow;

-> Search your computer -> Additional Drivers ->
Using X.Org X server - Nouveau display driver from xserver-xorg-video-nouveau (open source)  (default)
(see attached photo - additional_driver.png)

changed to:
Using NVIDIA binary driver -version 381.130 from nvidia-384 (proprietary, tested)
-> Apply Changes

Reboot

Now resolution 2560x1440 is available

Thanks

Regards
satimis

---

