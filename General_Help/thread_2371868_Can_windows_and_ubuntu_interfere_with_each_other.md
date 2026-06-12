---
title: "Can windows and ubuntu interfere with each other?"
date: 2017-09-19
forum: General Help
---

### Post by marco furio ferrario on 2017-09-19
I installed Ubuntu 17.04 (previously Ubuntu 16.04) and Windows 10 on a Dell xps 9550. 
During the last 12 months, I've experienced odd issues when I changed drivers in one OR the other operating system. 
My question is: how can drivers or any other change in one operating system can affect stability of the other OS?
Exemple:
One of the most well-known issue is the frequent blue screen and critical errors in Windows (and freezing in Ubuntu) due to the SSD drivers (apparently solved by installing 950 PRO drivers on windows). 
Shouldn't be the 2 OS independent? 

What do you suggest to keep stability?

Thank you

---

### Post by TheFu on 2017-09-19
Yes.  Different drivers might leave the registers inside different devices with different settings, so if you reboot, then those altered settings might be left.  This has been an issue for some NICs, due to the drivers, from time to time.  I've never seen this myself, but others in these forums have.  Usually, it is Windows screwing with Linux, because the vendors don't make their drivers with the same care for Linux as they do for Windows.  IMHO.  Intel is different. I've never heard of anyone have this issue with an Intel NIC.

If you want a stable system, don't change things that aren't broken or aren't security issues.  So - first of all - don't run 17.xx.  Stay on an LTS release.

Linux can usually see the storage for Windows, if you allow access (or request it).  It is possible, if that other storage is mounted, for a Linux user to delete Windows.  Similarly, it is possible for someone from Windows to wipe the partitions holding Linux.

There's always virtualization, which I use extensively.  My primary desktop runs inside a VM.

---

### Post by mastablasta on 2017-09-20
> **marco furio ferrario said:**
>  

What do you suggest to keep stability?



use one OS per machine. if you need the other use virtualization.

---

### Post by kc1di on 2017-09-20
Another area where there is some interaction is the clock, If Windows sets the machine clock to UTC and Linux to Local it will be reflected in the time being wrong when you boot back to linux or windows. Not sure about other settings, but for the most part there is not much interaction at the software level. only machine level.

and as one has pointed out above visualization can help.

---

### Post by Impavidus on 2017-09-20
I remember I had some issues with network or graphics card. After shutting down Windows and booting Ubuntu, it didn't work, but after booting Ubuntu again, it worked. But that was years ago, I think on Hardy Heron.

> **kc1di said:**
> If Windows sets the machine clock to UTC and Linux to Local it will be reflected in the time being wrong when you boot back to linux or windows.
Usually it's the other way around.

---

### Post by marco furio ferrario on 2017-09-21
Thank you for the answer. Do you mind quickly explaining how such things happen? I thought drivers are only programs that run on the basis of an operating system, not directly in contact with the hardware. Why do I have one bios for both OS but different drivers then? thank you

---

### Post by TheFu on 2017-09-21
Drivers aren't written by the same teams for different OSes. In the Linux world, drivers often have to be reverse engineered without the aid of the vendor who made the card/chips.  This can mean that memory in each chip isn't properly cleared on restart/initialization, so at reboot, when power isn't completely removed for sufficient time, those registers have left-over data.

All hardware for every OS is mapped to a location for the OS to have access to memory on those chips/cards/devices and to transmit calls, usually via APIs.  In Linux, device mappings are seen in files under /dev/

---

