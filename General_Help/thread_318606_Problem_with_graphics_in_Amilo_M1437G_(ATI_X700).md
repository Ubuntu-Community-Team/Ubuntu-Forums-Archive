---
title: "Problem with graphics in Amilo M1437G (ATI X700)"
date: 2006-12-14
forum: General Help
---

### Post by goraperas on 2006-12-14
Hi,
 
I am trying to install Ubuntu in my laptop **Fujitsu-Siemens Amilo M1437G **and there is no way to make it works. My problem is that I cannot start the graphics mode. I have read many guides, how-to´s and posts in the forums, but it is still not working. 

My card is an **ATI Radeon X700**.

I installed **Ubuntu 6.06 Dapper Drake**
I downloaded the drivers with **apt-get install xorg-driver-fglrx**
I edited the **/etc/X11/xorg.conf** and changed **"ati" to "fglrx"**
I restarted gdm with **/etc/init.d/gdm restart**
 
I also tried to install other versions of Ubuntu (5.10, 6.10) without good results and other distributions of Linux (Suse 10.0, Fedora 4) doesn´t even recognize the SATA hard disk, the keyboard of the laptop, or hangs up during the installation. 

Any help would be really really welcome.

Best regards,

goraperas

P.D. Some of the errors I get are:

**$ gdm restart**
--> [...] Failed to start the X server [...] 
--> [...] The X server is now disabled. Restard GDM when it is configured correctly [...] 

**$ startx**
--> [...] Fatal server error: no screens found [...]

**$ fglrxinfo**
--> bash: fglrxinfo: No such file or directory

---

