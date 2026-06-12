---
title: "Screen freeze and System hang."
date: 2015-09-15
forum: General Help
---

### Post by swapnil10 on 2015-09-15
Yesterday, I installed **Xubuntu 14.04 (32-bit)**, but sometimes, the **mouse pointer stops to move and the screen freezes suddenly**. It **happens with** almost all linux distros including l**ight-weight distros** too.

My **system configuration** is as follows:

**Processor**- AMD Athlon(tm) II X2 240 Processor,  MMX,  3DNow (2 CPUs), ~2.8GHz
**Memory**- 1792MB (~2GB)
**DirectX Version**: DirectX 9.0c (4.09.0000.0904)

**Display**- Card name: NVIDIA GeForce 6150SE nForce 430           Manufacturer: NVIDIA
           Chip type: GeForce 6150SE nForce 430
           DAC type: Integrated RAMDAC
           Device Key: Enum\PCI\VEN_10DE&DEV_03D0&SUBSYS_CB8410DE&REV_A2
           Display Memory: 512.0 MB
           Current Mode: 1360 x 768 (32 bit) (60Hz)
           Monitor: Plug and Play Monitor
           Monitor Max Res: 1600,1200
           Driver Name: nv4_disp.dll
           Driver Version: 6.14.0011.7516 (English)
           DDI Version: 9 (or higher)
           Driver Attributes: Final Retail
           Driver Date/Size: 5/2/2008 20:16:00, 6108160 bytes

Using dual boot system with Windows at present..!!

---

### Post by CharlesA on 2015-09-15
Sounds like X crashed, but I don't really know what you'd need to do to check for it.

Do you experience the same problems in Windows?

---

### Post by swapnil10 on 2015-09-15
No.. I face this only in Linux..!!

---

### Post by VMC on 2015-09-15
Here's the problem "**NVIDIA GeForce 6150SE nForce 430**".

I have that same integrated video on my system. You need to edit grub, at the end of the "*linux*" line, add *nomodeset*, then push F10. When when booted install nvidia driver.

edit: Go [HERE]("http://askubuntu.com/questions/47506/how-do-i-install-additional-drivers") , follow the "Additional Drivers" of the OS you installed.

---

### Post by swapnil10 on 2015-09-16
How to edit the grub? Is it obligatory to first edit the Grub and then install the additional drivers? Does this order matters?

---

### Post by swapnil10 on 2015-09-16
The "Additional Drivers" search gave this result. Not edited grub yet.

---

### Post by VMC on 2015-09-16
What that image shows is that you have *Nouveau* installed. You need to select the top choice (tested), for it to be installed.

---

### Post by swapnil10 on 2015-09-18
Problem Solved. Thank you :D

---

