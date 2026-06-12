---
title: "Black screen after update and upgrade"
date: 2024-01-16
forum: General Help
---

### Post by SUPERFITTER on 2024-01-16
I just updated and upgraded  Ubuntu.  When I rebooted I had a black  screen. I rebooted again and had the same results.  
I tried Advanced options for Ubuntu then Recovery Mode and then Resume normal boot.  Now I get a full bootup.  
When I either reboot or start the computer I still get a Blank screen.  If I reboot into the recovery mode I get a full desktop screen.  
Is there any way  to repair this problem?

Thank you

---

### Post by MAFoElffen on 2024-01-16
Do you have a NVidia GPU and drivers installed? Which release version of Ubuntu? Which Kernel?

Go through Recovery > Resume... is the same as adding 'nomodeset' to the boot parameters...

---

### Post by SUPERFITTER on 2024-01-16
Ubuntu 22.04.3 LTS x86_64 
Kernel: 5.15.0-91-generic 
I have a GPU: NVIDIA GeForce GT 520 
Using NVIDIA driver metapackage from nvidia-driver-390(proprietary, tested)

---

### Post by MAFoElffen on 2024-01-16
Use the second option in the Grub2 menu > "Advanced Options For Ubuntu" > Boot a recovery option.

When you get to the Recover menu > network > root...

When you et to the Root prompt , hit the <Enter> key to get into maintenant mode...
```

apt update
apt remove --purge nvidia* libnvidia*
apt install nvidia-driver-390 nvidia-dkms-390
reboot

``` 
Test

---

### Post by SUPERFITTER on 2024-01-17
I scrolled down to network and clicked on it, it ran some lines on a terminal-like screen at the bottom of the window and then it rebooted.  I never did see the root.  I went to additional drivers and switched to the open-source driver, everything looked the same as the Nvidia driver desktop.

---

### Post by MAFoElffen on 2024-01-17
And if you reinstalled the Nvidia driver from there (after that) did it come back?

---

### Post by SUPERFITTER on 2024-01-17
No.  I tried to install the Nvidia driver again.  It buffered as I tried to install it, but about three quarters of the way it stopped and went back to the open-source driver.  I tried twice and had the same results.

---

### Post by MAFoElffen on 2024-01-19
What happens and what does it show if you open a terminal window and do
```

sudo ubuntu-drivers list

```

---

### Post by SUPERFITTER on 2024-01-21
$ sudo ubuntu-drivers list
[sudo] password for me: 
nvidia-driver-390, (kernel modules provided by nvidia-dkms-390)

---

