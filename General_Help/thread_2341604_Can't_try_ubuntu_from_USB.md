---
title: "Can't try ubuntu from USB"
date: 2016-10-29
forum: General Help
---

### Post by spennet on 2016-10-29
My PC is running Windows 10 with Intel i7-6700K

I have the ubuntu iso on USB using rufus. When I boot into the usb I choose "try ubuntu". After that a screen shows that I suppose indicates that ubuntu is loading. After that my monitor gets no signal and I get no output on the screen whatsoever. I have tried using other ways of writing the iso to the usb as well as other usb ports but it is not working. I also had this problem when trying the same thing with another Linux distro (Arch Linux).

---

### Post by sudodus on 2016-10-29
Welcome to the Ubuntu Forums :-)

I suspect that there is a problem with the graphics card. If that is the case, it might help with some boot option. You can start with **nomodeset** according to this link and links from it,

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

It will help us help you, if you tell us as much as possible about the computer hardware, so at least, please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by spennet on 2016-10-29
First of all, thank you for the quick reply! :)

I now tried to press a key after I chose "try ubuntu without installation" in order to access the advanced welcome page options. This didn't work, nothing showed up. Is this the only way I can set boot options if I'm not using grub?

My specs are:

- Custom built desktop PC
- Intel i7-6700k @ 4.00GHz
- 16 GB RAM
- Nvidia GeForce GTX 970
- ASUS PCE-N15 11n Wireless LAN PCI-E Card

---

### Post by sudodus on 2016-10-29
In BIOS mode: Press a key in the very beginning, while there are two small icons at the bottom of a red screen.

In UEFI mode: Press 'e' when you see the grub menu (white text on black background).

---

### Post by sudodus on 2016-10-29
You will probably need **nomodeset** with that graphics card, as with many nvidia cards. And after installing Ubuntu, you should install a proprietary driver for the card.

It might help if you also specify the ***motherboard***. There are helpers here, who know specific issues and work-arounds for some card brands names and/or models.

---

### Post by spennet on 2016-10-31
Thank you!

Now I've been able to try ubuntu from usb and also install it. However, I'm having huge problems with installing the nvidia drivers and getting stuck in the infamous "login loop" after installing the drivers. Seems like there's no sure way of solving that :(

---

### Post by sudodus on 2016-11-01
Try the following link and links from it. I think it will help you install a proprietary driver for your nvidia card,

[BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by spennet on 2016-11-01
Thanks!

I got passed the login loop by disabling secure boot after installing the driver :)

---

### Post by sudodus on 2016-11-01
Congratulations and thanks for sharing your solution :-)

---

