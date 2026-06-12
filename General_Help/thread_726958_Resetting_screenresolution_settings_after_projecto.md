---
title: "Resetting screen/resolution settings after projector use"
date: 2008-03-17
forum: General Help
---

### Post by IrishPidge on 2008-03-17
I recently installed Ubuntu and it was working perfectly. I had to use a projector (through the VGA port) for a presentation. I plugged in the projector and rebooted. Ubuntu loaded up the two desktops. Now that I'm done with the projector, I can't get Ubuntu looking the way it did previously. I've tinkered with screen and resolution settings, but it still looks ugly.

Is there any way to reset Ubuntu to the screen/resolution settings it had when it installed?

I'd really appreciate any help.

---

### Post by gobbles414 on 2008-03-17
> **IrishPidge said:**
> I recently installed Ubuntu and it was working perfectly. I had to use a projector (through the VGA port) for a presentation. I plugged in the projector and rebooted. Ubuntu loaded up the two desktops. Now that I'm done with the projector, I can't get Ubuntu looking the way it did previously. I've tinkered with screen and resolution settings, but it still looks ugly.

Is there any way to reset Ubuntu to the screen/resolution settings it had when it installed?

I'd really appreciate any help.

If neither *System => Administration => Screens and Graphics* nor *System => Preferences => Screen Resolution* are able to solve your problem, type *sudo dpkg-reconfigure xserver-xorg* into the command line (*Applications => Accessories => Terminal*). Alternativly, you can type the same command into Ubuntu's "Rescue Mode". That procedure is as follows:

1. Look closely for either a GRUB menu or a GRUB countdown as your computer boots.
2. If you see the countdown, press the escape button on your keyboard.
3. In GRUB, choose the Rescue Mode for your highest kernel version. Allow Rescue Mode to boot.
4. Type *sudo dpkg-reconfigure xserver-xorg* and press enter on your keyboard.
5. Follow the instructions in the wizard. When you're done, type *sudo reboot* and press enter.
6. Boot normally and log into Ubuntu.

Does this help?

---

### Post by IrishPidge on 2008-03-17
> **gobbles414 said:**
> If neither *System => Administration => Screens and Graphics* nor *System => Preferences => Screen Resolution* are able to solve your problem, type *sudo dpkg-reconfigure xserver-xorg* into the command line (*Applications => Accessories => Terminal*). Alternativly, you can type the same command into Ubuntu's "Rescue Mode". That procedure is as follows:

1. Look closely for either a GRUB menu or a GRUB countdown as your computer boots.
2. If you see the countdown, press the escape button on your keyboard.
3. In GRUB, choose the Rescue Mode for your highest kernel version. Allow Rescue Mode to boot.
4. Type *sudo dpkg-reconfigure xserver-xorg* and press enter on your keyboard.
5. Follow the instructions in the wizard. When you're done, type *sudo reboot* and press enter.
6. Boot normally and log into Ubuntu.

Does this help?
Thanks for replying. I'm afraid that that didn't help. I went through the wizard, but it wasn't able to autodetect the settings, so I had to manually configure in low-graphics mode, which leaves me with the same problem. Any information on the laptop I should provide?

---

### Post by Fire_Chief on 2008-03-17
What video chipset and drivers are you using?

---

### Post by gobbles414 on 2008-03-17
> **IrishPidge said:**
> Thanks for replying. I'm afraid that that didn't help. I went through the wizard, but it wasn't able to autodetect the settings, so I had to manually configure in low-graphics mode, which leaves me with the same problem. Any information on the laptop I should provide?

Neither *System => Administration => Screens and Graphics* nor *System => Preferences => Screen Resolution* worked for you...? That's strange. In the wizard, your safest choice is VESA. Fire_Chief is correct about the info that you'll need to provide. And if your laptop uses a graphics card, please provide a brand and model number too. You might also try going *System => Administration => Restricted Drivers Manager* and enabling any graphics-related items in the list. Did that help?

---

