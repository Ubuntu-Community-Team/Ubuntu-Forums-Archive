---
title: "Graphics Card Not Detected by X Server"
date: 2008-01-22
forum: General Help
---

### Post by ketzerei on 2008-01-22
I just recently decided to give Kubuntu a try, seeing as I wanted to go outside GNOME for a bit, and have run into a problem. I installed Kubuntu last satruday, with no hiccups, no flaws, nothing. However, I had a problem where my KDE panel at the bottom of the screen, would vanish permenently, and wouldn't come back even after I rebooted. So, I tried deleting the .kde config folder in my home directory. I rebooted and tried to log in, and got an error. Something about a dcon server or something like that not working or running, so I reinstalled Kubuntu, and now X won't detect my ATI card. I can install the drivers and everything just fine, but when I run 'dpkg-reconfigure xserver-xorg' it says no suitible X server detected for my card. HELP!

---

### Post by por100pre1 on 2008-01-23
Depending of your card, it can use one of these drivers (these are NOT all possible drivers):
**ati**, **fbdev**, **r128**, **radeon**, **vesa**, or **vga**. 
Which card are you using? :-k

---

### Post by ketzerei on 2008-01-23
ATI Radeon X1600 PRO. When I select the ATI driver tho too, it gives me this error like it doesnt detect the radeon chip.

---

### Post by aldenhg on 2008-01-23
Try going to ATi's website and downloading their driver installer. Alternately you can install it from the Restricted Drivers manager or from Synaptic.

---

### Post by ketzerei on 2008-01-25
Well, it seems to have fixed itself, so I guess I just had a broken install. I just have one final question, is there any patches or tips or anything like that I can use to un-crapify my card? ATI's drivers blow, so I am getting an NVIDIA card, but until then I would like to know if anyone has any suggestions to make it run better or if I have to tough it out till I get my new card. Thanks in advance.

---

