---
title: "splash screen not loading...?"
date: 2008-05-06
forum: General Help
---

### Post by magicmanfk on 2008-05-06
Hey, I'm a new linux user (not very competent), and I've recently been attempting some customization. I tried messing around with the usplash stuff, and somewhere I must have messed something up, because now it doesn't even bother showing a splash screen and just does the loading/shutting down text. I'm using hardy heron. I've tried a bunch of stuff.

When I go to terminal and type "sudo usplash -c" it shows a splash screen, although I don't think it's the same one that I set to when I ran "sudo update-alternatives --config usplash-artwork.so". The problem might have come from trying to install one of the usplash themes "fingerprint" something or another. In the readme it said to add "vga=791" to a specific part in the text file /boot/grub/menu.lst. I made those changes but when it didn't work I changed it back. Any help would be greatly appreciated!

Thanks,
Franklin

---

### Post by mano cazalet on 2008-05-06
i think the easiest way to manaege usplash themes is by start-up manager

You can install it

sudo apt-get install startupmanager

after that it will be accessible in system - administration menu

---

### Post by magicmanfk on 2008-05-06
unfortunately, I have already installed that and tried to change the splash screen there, but even after changing it no image shows during startup/shutdown. Thanks for the idea though!

---

### Post by tommyhakinen on 2008-05-06
Does it mean that it only showing all the command running during the boot time? Like when you boot from the Recovery Mode then straight to the Login Window? If that's what happening, you may try this.

Open Startup-Manager, under the "Boot Option" tab, check if "Show boot splash" Under "Misc" is checked. If it's not checked, please check it. Then restart your system.

Good luck

Regards,

tommy

---

### Post by magicmanfk on 2008-05-07
actually, I finally got it to work. If anyone else gets the problem, here's what I did: 

Ran "sudo update-grub" in terminal and it noticed that the menu.lst file had been locally edited, so it gave me multiple options, and I chose to update to the default. That seemed to fix it. 

Thanks again for all the help! I'm really digging the whole ubuntu thing.

~Franklin

---

