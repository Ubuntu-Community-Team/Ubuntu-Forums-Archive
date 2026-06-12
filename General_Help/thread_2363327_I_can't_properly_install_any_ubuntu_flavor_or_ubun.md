---
title: "I can't properly install any ubuntu flavor or ubuntu itself."
date: 2017-06-08
forum: General Help
---

### Post by sadpotato on 2017-06-08
Every time I try to install Ubuntu I usually get system errors. If I try to install any linux distro out there I always get a black screen with fast moving text that is unreadable I think it says something about PCIe. I would really like to use ubuntu but this always happens.


This is what stays at an infinite loop :
[ATTACH=CONFIG]275539[/ATTACH]
I would like to use linux but I am always forced to switch back to windows because of this.

---

### Post by QIII on 2017-06-09
Hello!

It might be helpful if you would tell us some details about your hardware, how you are preparing your installation media, how you are trying to install, whether the installation process appears to complete, etc.

---

### Post by sadpotato on 2017-06-09
I am able to install the OS by using rufus and putting it on a USB but when I reboot or try to shut down my computer that screen appears sometimes and at other times it doesn't.

My specs:
GTX 970
i5-6400
8GB of DDR4 Ram
7200 RPM HDD
PCIe GBE Family Controller 
Realtek 8821AE Wireless Card.

---

### Post by Bucky Ball on 2017-06-09
Welcome. Think you need to use the 'nomodeset' option at boot when installing. I have the same GTX 970 card and that is what I did from memory (and what others here have done). 

To do this, and also from memory (QIII may be able to confirm the accuracy of this or otherwise), when you boot from the install media and get to the Ubuntu purple screen with the icon at the start of the boot, hit shift (may be escape depending on if you've booted in UEFI or legacy) and that should take you to a screen with F1 - F6 (F8?) pop-up menus along the bottom.

Hit F6 on your keyboard and choose the 'nomodeset' option then proceed with 'Try Ubuntu'. That will (should) get you to the 'Try Ubuntu' desktop; a live session.

From here you can install using the icon on the desktop. Once you have installed and on the first boot, once you are at a desktop, do an update and then check 'Additional Drivers'. There will be an NVidia driver there for your GTX 970. It will have (recommended) next to it. You DO NOT need to download drivers from the NVidia site or any other third-party site. The one in 'Additional Drivers' works fine with that card and you can tweak around with newer version (at your own risk) later if you're inclined to.

If at any time during trying to install you hit the blank screen or no screen, try again and use the nomodeset option. You can also add the option post-install if you are having problems booting the install. We can help you with that if you get to that point. You may not need to do that when you get there.

The GTX 970, and other NVidia cards, work brilliantly on Ubuntu with the NVidia driver installed. Just a matter of getting to the point where you can install it! 

Hope that helps and good luck. ;)

---

### Post by sadpotato on 2017-06-09
> **Bucky Ball said:**
> Welcome. Think you need to use the 'nomodeset' option at boot when installing. I have the same GTX 970 card and that is what I did from memory (and what others here have done). 

To do this, and also from memory (QIII may be able to confirm the accuracy of this or otherwise), when you boot from the install media and get to the Ubuntu purple screen with the icon at the start of the boot, hit shift (may be escape depending on if you've booted in UEFI or legacy) and that should take you to a screen with F1 - F6 (F8?) pop-up menus along the bottom.

Hit F6 on your keyboard and choose the 'nomodeset' option then proceed with 'Try Ubuntu'. That will (should) get you to the 'Try Ubuntu' desktop; a live session.

From here you can install using the icon on the desktop. Once you have installed and on the first boot, once you are at a desktop, do an update and then check 'Additional Drivers'. There will be an NVidia driver there for your GTX 970. It will have (recommended) next to it. You DO NOT need to download drivers from the NVidia site or any other third-party site. The one in 'Additional Drivers' works fine with that card and you can tweak around with newer version (at your own risk) later if you're inclined to.

If at any time during trying to install you hit the blank screen or no screen, try again and use the nomodeset option. You can also add the option post-install if you are having problems booting the install. We can help you with that if you get to that point. You may not need to do that when you get there.

The GTX 970, and other NVidia cards, work brilliantly on Ubuntu with the NVidia driver installed. Just a matter of getting to the point where you can install it! 

Hope that helps and good luck. ;)

I know about nomodeset and I never once mentioned a problem with a blank screen. I said I have problems when restarting my computer and shutting it down and attached a picture of it. I was able to install Ubuntu but I get a black screen with white letters that just stay on a loop and I need to turn off my computer using the power button to get rid of it the text goes so fast the letters overlap each other but I think it says something about PCIe.

---

### Post by Bucky Ball on 2017-06-10
Ok. Good luck with it, then. ;)

---

