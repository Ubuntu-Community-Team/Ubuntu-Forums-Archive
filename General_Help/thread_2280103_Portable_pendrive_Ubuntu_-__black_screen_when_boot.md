---
title: "Portable pendrive Ubuntu -  black screen when booting on nvidia optimus system"
date: 2015-05-28
forum: General Help
---

### Post by r-m-r--epe on 2015-05-28
Hey guys,

i got a problem. I have installed Ubuntu 14.02 on a pen drive as an complete install. It is working fine here on a desktop Pc but when i try the usb on a lenovo y500 laptop it only shows a black screen. I have already checked in the bios and it is on legacy and usb boot is also supported. I have had no problems with different kind of portable installations as in windows 10, which i had a couple of days ago.

Anyone has a suggestion on how to fix this?

Kind regards and many thanks in advance.

Roel

---

### Post by coffeecat on 2015-05-28
Welcome to the forum.

This could be a graphics device and/or driver problem. What is the graphics card on your desktop machine, and have you installed a proprietary driver?

A quick google search tells me that the Lenovo Y500 has "NVIDIA® GeForce® GT 650M dedicated graphics with NVIDIA® Optimus™ technology". Please confirm that this is so.

I have no experience of Nvidia Optimus, but know that it can be problematic. If you can confirm the above details then, hopefully, someone with experience of Optimus may be able to help you.

---

### Post by r-m-r--epe on 2015-05-28
Thanks for the quick reply. And yes indeed it is the geforce Gt650m. When i look for devices in Ubuntu it gives me this while running on the desktop: Gallium 0.4 on AMD CEDAR. It is an on board graphics card. I will try to google about these problems with optimus. and i will see if i can find a fix for it. 

Thanks 
Roel

---

### Post by coffeecat on 2015-05-28
I've edited your thread title to include the keyword optimus – hopefully that will attract someone who can help with that aspect.

> **r-m-r--epe said:**
> When i look for devices in Ubuntu it gives me this while running on the desktop: Gallium 0.4 on AMD CEDAR. It is an on board graphics card.

You didn't actually answer my question about whether or not you installed a proprietary driver. With your AMD graphics, the default open source driver will be OK, but if you installed the proprietary fglrx driver, that will cause problems when trying to boot on a system with nvidia graphics. So that we can be sure, please post the output of this terminal command:

```
sudo lshw -C video
```

---

