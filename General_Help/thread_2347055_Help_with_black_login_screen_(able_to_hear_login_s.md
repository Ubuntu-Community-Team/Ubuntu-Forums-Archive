---
title: "Help with black login screen (able to hear login sound) - all Nvidia drivers"
date: 2016-12-21
forum: General Help
---

### Post by ac2334 on 2016-12-21
Hello,

Need some serious help with this frustrating problem. 

I own an MSI GT 780DX with a GTX 570M and I would really like to have Ubuntu running on it. I have attempted to get 16.10 and 16.04 working with no success. 

I can get through the installation without issues, but the problem is when I install the Nvidia drivers for this card. Immediately after rebooting I get to the login screen (I know that I am there because I can hear the login sound effect) but I can't see the screen no matter what (only black). If I go the TTY with ctrl+alt+f1 it usually works (depends on the driver) and I can purge the Nvidia drivers, but the problem still remains.

I have tried blacklisting nouveau, renaming xorg.conf, installing 7 or 8 different Nvidia drivers (both from within Additional Drivers and directly from Nvidia as .run files.) - Nothing is working.

The only time I am able to see the login screen on an Nvidia driver is if I have installed the "legacy" 304 driver - then I can see the login screen, but I enter into a login loop (screen will flash after entering password and then 5 seconds later it puts me right back to the login page)

Does anyone know how to fix this? I suspect that there is a deeper problem blocking the Nvidia driver from working that only occurs post-driver installation - the purging of the driver does nothing to fix the black screen.

Thank you

---

### Post by hrhthegreat on 2016-12-22
> **ac2334 said:**
> Hello,

Need some serious help with this frustrating problem. 

I own an MSI GT 780DX with a GTX 570M and I would really like to have Ubuntu running on it. I have attempted to get 16.10 and 16.04 working with no success. 

I can get through the installation without issues, but the problem is when I install the Nvidia drivers for this card. Immediately after rebooting I get to the login screen (I know that I am there because I can hear the login sound effect) but I can't see the screen no matter what (only black). If I go the TTY with ctrl+alt+f1 it usually works (depends on the driver) and I can purge the Nvidia drivers, but the problem still remains.

I have tried blacklisting nouveau, renaming xorg.conf, installing 7 or 8 different Nvidia drivers (both from within Additional Drivers and directly from Nvidia as .run files.) - Nothing is working.

The only time I am able to see the login screen on an Nvidia driver is if I have installed the "legacy" 304 driver - then I can see the login screen, but I enter into a login loop (screen will flash after entering password and then 5 seconds later it puts me right back to the login page)

Does anyone know how to fix this? I suspect that there is a deeper problem blocking the Nvidia driver from working that only occurs post-driver installation - the purging of the driver does nothing to fix the black screen.

Thank you 
I have exact same issue with nvidia 920 mx on asus. I created a thread in nvidia linux forum : [https://devtalk.nvidia.com/default/topic/983234/linux/black-screen-after-installing-nvidia-driver-on-920mx/](https://devtalk.nvidia.com/default/topic/983234/linux/black-screen-after-installing-nvidia-driver-on-920mx/)
Did you try with 4.9 kernel?

---

### Post by gordintoronto on 2016-12-22
Have you tried nomodeset? See the Community Documentation for how to do it.

---

### Post by ac2334 on 2016-12-29
Here is where I am with this:

Currently only able to run at 1024x768 using the Xorg Nouveau driver and that's ONLY if nomodeset is active in grub..

I need to have graphics acceleration back...anyone please..

Hrhthegreat - has anyone gotten you any further in the Nvidia forums? Could changing the kernel potentially fix it?

There must be a way to narrow down what is causing the issue, but I need some help with this. My system only has a GTX 570M, no other on-board card at all.

Thanks

---

### Post by hrhthegreat on 2017-01-10
I've found that the secure boot should be turned off from BIOS. I did this and now it's working.
> **ac2334 said:**
> Here is where I am with this:

Currently only able to run at 1024x768 using the Xorg Nouveau driver and that's ONLY if nomodeset is active in grub..

I need to have graphics acceleration back...anyone please..

Hrhthegreat - has anyone gotten you any further in the Nvidia forums? Could changing the kernel potentially fix it?

There must be a way to narrow down what is causing the issue, but I need some help with this. My system only has a GTX 570M, no other on-board card at all.

Thanks

---

