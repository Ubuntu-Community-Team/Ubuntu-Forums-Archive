---
title: "fglrxinfo fails"
date: 2008-03-17
forum: General Help
---

### Post by Max Carey on 2008-03-17
Installed proprietary ATI drivers, but the output from fglrxinfo is
```
Error: Unable to open display (null)
```
Any ideas? I've done a lot of searching, but haven't found anybody else with this problem.

---

### Post by DoctorMO on 2008-03-17
How did you run it? try running it from the gui terminal instead of from one of the VTs..

---

### Post by Ub1476 on 2008-03-17
Graphic card?

```
lspci | grep VGA
```

---

### Post by GSMD on 2008-06-26
Well, basically got the very same thing.
Converted
```
fglrx-amdcccle_8.501-0ubuntu1_amd64.deb
fglrx-kernel-source_8.501-0ubuntu1_amd64.deb
xorg-driver-fglrx_8.501-0ubuntu1_amd64.deb
xorg-driver-fglrx-dev_8.501-0ubuntu1_amd64.deb

```and installed them. Ran
```
sudo aticonfig --initial
```Rebooted.
```

$ lsmod | grep fg
fglrx                2000708  0
$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]

```Still,
```
$ fglrxinfo
Error: unable to open display (null)
```Here's the section from generated xorg.conf:
```
Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:5:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
```Any ideas? I'll keep digging...

---

