---
title: "Choosing primary display on radeon open source drivers"
date: 2013-09-22
forum: General Help
---

### Post by Fanas on 2013-09-22
Is there a way to setup a primary display on open source drivers for radeon. Now login screen is always displayed on my tv instead of monitor, also all the notifications are displayed there but not on the monitor.

---

### Post by dcstar on 2013-09-26
> **Fanas said:**
> Is there a way to setup a primary display on open source drivers for radeon. Now login screen is always displayed on my tv instead of monitor, also all the notifications are displayed there but not on the monitor.

```
sudo gedit /etc/X11/xorg.conf 
```
Find the code blocks that look similar to these (from my system) and add in the highlighted lines, then save the changes and reboot:
```
Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "Disable" "false"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
**    Option        "Primary" "false"**
EndSection

Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
**    Option        "Primary" "true"**
EndSection
```
On my system the first listing was for my HDMI output and the second was for my DVI monitor, prior to making this change everything went to the HDMI as the default primary output, now the DVI monitor is the Primary display.

---

### Post by Fanas on 2013-09-27
No such file is available.

---

### Post by dcstar on 2013-09-27
Install the **fglrx-updates** & **fglrx-amdcccle-updates** packages, then:

```
sudo amdconfig --initial
```

Now you should have a xorg.conf file.

---

### Post by Fanas on 2013-09-28
> **dcstar said:**
> Install the **fglrx-updates** & **fglrx-amdcccle-updates** packages, then:

```
sudo amdconfig --initial
```

Now you should have a xorg.conf file.

Proprietary drivers for my card sucks so much. Isn't there a way for open source drivers?

---

