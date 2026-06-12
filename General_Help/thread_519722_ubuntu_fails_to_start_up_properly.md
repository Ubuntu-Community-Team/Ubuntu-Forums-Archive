---
title: "ubuntu fails to start up properly"
date: 2007-08-07
forum: General Help
---

### Post by DishBreak on 2007-08-07
Hello all,

I'm experiencing not 1, but 2 problems on my computer. 

1) **Monitor goes black/shuts off ** This is what happens 80% of the time. Basically, GRUB starts okay, but when I choose Ubuntu 2.6.11, the thing starts to load and then goes black. It seems like my monitor stops receiving a signal, because it checks both inputs for a signal and then goes into standby mode. I have a feeling that the culprit might be my Radeon 9250, but I'm not sure.

2) **Ubuntu is REALLY slow** This happens on the rare occasion that Ubuntu decides to start up. Everything lags and the computer takes an eternity to start up and load once I log in. Of course, once I reboot, I'm met with problem number 1.

please, somebody help me out. how do I start to tackle this problem.

---

### Post by dougfractal on 2007-08-07
> **DishBreak said:**
> Hello all,

I'm experiencing not 1, but 2 problems on my computer. 

when I choose Ubuntu 2.6.11,


install  feisty as  from the kernel version I think you are on dapper or breezy.

or 
sudo apt-get dist-upgrade

> 
 Radeon 9250, but I'm not sure.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by DishBreak on 2007-08-07
Thanks for the quick response.

Okay, I see there's a bug for dvi output. 

please excuse my incompetency. I clearly cited the wrong kernel :oops:
I am definetly using feisty. Should I be entering a recovery mode from GRUB, instead of letting it load the first entry?

---

### Post by dougfractal on 2007-08-07
So the liveCD worked?

if so use the xorg.conf file from that.

---

### Post by DishBreak on 2007-08-08
Sorry? I don't quite understand what you mean.

---

### Post by dougfractal on 2007-08-08
Have you done anything to the xorg file to get 3D acceleration?

if so reset the xorg file
sudo dpkg-reconfigure -phigh xserver-xorg

or does this help?
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

backup
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
```

so ```
sudo gedit /etc/X11/xorg.conf
```
change the Section "Device" 
but also mod your xorg.conf
```
Section "Device"
Identifier "Radeon"
Boardname "ATI Technologies, Inc. Radeon 9250"
VendorName "ATI Technologies"
Driver "radeon"
BusID "PCI:1:0:0"
Option "RenderAccel" "true"
Option "AGPMode" "4"
Option "AGPFastWrite" "true"
Option "EnablePageFlip" "True"
Option "UseInternalAGPGART" "no"
Option "backingstore" "true"
Option "AllowGLXWithComposite" "true"
EndSection
```

make sure device is "screen"  is correct.
> Section "Screen"
        Device          "radeon"

---

