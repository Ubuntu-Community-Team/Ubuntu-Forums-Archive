---
title: "System Freezes Periodically After Installing 17.10"
date: 2017-11-03
forum: General Help
---

### Post by gauss4563 on 2017-11-03
Hi,

So I installed Ubuntu 17.10 (clean) a few days ago and had the system freeze periodically, so I reinstalled it (many times since). 
I use Nouveau drivers for nvidia GTX 970 card because the nvidia drivers mess everything completely (tearing when first installing and then the system just won't launch)
I also use GNOME 3.26 and Wayland and the problem seems to be quite frequent among 17.10 users, but I could find any solution. 

Do you have any suggestions how to fix this? Or at least to find out what causes it?
**The system freezes completely and I have to use REISUB in order to reboot. Alt+F2 \ Ctrl+Alt+F1 Doesn't work. Audio will still play in the background but the image is completely frozen. 
It can happen after 20mins of usage, or 3 hours. Seems like maximizing\minimizing video windows accelerates this, for it happens many times just when I double click a video.

Thanks in advance!

---

### Post by gauss4563 on 2017-11-04
Anyone? 
Please?
This is really important for me, for it interferes with a project I work on.

---

### Post by mörgæs on 2017-11-04
> **gauss4563 said:**
> 
I also use GNOME 3.26 and Wayland and the problem seems to be quite frequent among 17.10 users


It is indeed. I suggest X/Lubuntu.

---

### Post by RobGoss on 2017-11-04
What are the specs for your machine it will help to pin point the issus

---

### Post by gauss4563 on 2017-11-04
> **RobGoss said:**
> What are the specs for your machine it will help to pin point the issus
***
Anything else required?

> [COLOR=#000000]It is indeed. I suggest X/Lubuntu.[/COLOR]

Does it mean to only change the environment from GNOME to LXDE?
Is there no more aesthetically pleasing solution?

---

### Post by gauss4563 on 2017-11-06
The workaround seems to be to just log in with Xorg instead of Wayland.

---

