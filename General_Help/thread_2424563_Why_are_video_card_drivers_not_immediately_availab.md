---
title: "Why are video card drivers not immediately available after installation?"
date: 2019-08-10
forum: General Help
---

### Post by maxj345 on 2019-08-10
I recently installed Ubuntu 18.04.2 on my computer. I noticed upon first login, that the video card drivers were not immediately available. Why is that?

Here is my hardware:

[INDENT]```
CPU: AMD Ryzen 3700X
Motherboard: ASUS X570 Pro
Memory: Corsair Vengeance LPX 16GB (2x8GB) DDR4 (CMK16GX4M2B3200C16)
Video Card: EVGA GeForce GTX 1660 XC Ultra GAMING (06G-P4-1167-KR)
Storage: Samsung 860 EVO 500 GB
```
[/INDENT]
 
I prepared the installation media using Rufus:

[https://i.imgur.com/UMECETZ.png](https://i.imgur.com/UMECETZ.png)
[SIZE=1] Preparing installation media in Rufus.[/SIZE]

Here is the setup I chose for the installation itself:

[https://i.imgur.com/CwBbQiM.png](https://i.imgur.com/CwBbQiM.png)
[SIZE=1]Setting up the installation.
[/SIZE]
[https://i.imgur.com/hwbX1WN.png](https://i.imgur.com/hwbX1WN.png)
[SIZE=1] Partitioning the drive.[/SIZE]

Here is what I observed upon first login to the system:

[https://i.imgur.com/U4TK2MO.png](https://i.imgur.com/U4TK2MO.png)
[SIZE=1]Video card drivers are not available upon first login into the system.[/SIZE]

So after connecting to the network, I did an update:

[INDENT]```
 sudo apt-get update
```
[/INDENT]
 
And that made the video card drivers available:

[https://i.imgur.com/t2vVECF.png](https://i.imgur.com/t2vVECF.png)
[SIZE=1]Video card drivers are now available after an update.[/SIZE]

Once I selected the proprietary drivers (NVIDIA driver metapackage from nvidia-driver-430), my installation was much snappier and set to the correct resolution:

[https://i.imgur.com/S7lBNRi.png](https://i.imgur.com/S7lBNRi.png)
[SIZE=1] System seems to be working properly now.[/SIZE]

I've read up on the Hardware Enablement ([HWE]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")) Stack that Ubuntu desktop ships with. Shouldn't that come with the drivers compatible with the video card? Is my understanding of HWE incorrect? Is HWE included in the installation of Ubuntu 18.04.2?

Is the hardware too recent? I know the Nvidia GeForce GTX 1660 was only released a few months ago.

---

### Post by ajgreeny on 2019-08-10
Please do not add huge images in the text as you originally did here; either add them as links as I have now done or add the images as attachments using the paperclip icon in the toolbar of the text entry box.  If using the **Quick Reply** button go to **Advanced** to see the full toolbar.

There are many users who use the forum on small screen phones etc, and there are still some who have limited and costly connections to the web; including large images will mean they do not even wait for the page to load.

---

### Post by maxj345 on 2019-08-10
Sorry about that. I will make sure to so from now on!

---

### Post by deadflowr on 2019-08-10
Most likely the apt-get update function never properly ran during the installation.

---

### Post by Yellow Pasque on 2019-08-11
> **maxj345 said:**
> Is my understanding of HWE incorrect? Is HWE included in the installation of Ubuntu 18.04.2?

HWE does not affect the proprietary nvidia driver. It only affects the open-source "nouveau" driver, since that is part of the kernel and uses mesa for 3D. Unfortunately, nouveau is not really suitable for cards newer than GTX750 because of lack of signed firmware.

---

### Post by him610 on 2019-08-11
It has been several weeks since my most recent install. If I remember correctly, during the installation process we are give the choice (checkboxes) as to whether we want updates and 3rd party drivers installed which should address your issue.

---

