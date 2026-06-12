---
title: "Ubuntu 11.04 stuck at loading screen forever"
date: 2013-04-12
forum: General Help
---

### Post by Zeast42 on 2013-04-12
I was updating from 11.04 to the newest release yesterday when I fell asleep. When I woke up, my screen was frozen on a screen during "Installing files" on the upgrade.

Ctrl Alt F1 didn't work, so I manually restarted my computer.

I start Ubuntu through Grub this morning, and it stays at the 4 dot loadscreen for minutes without doing anything. 
Someone says this coupd be a filesystem check, so I let it run while I take a shower. I come back to another frozen screen.

I now open Recovery Mode. When I originally tried to navigate through it, each arrow key or enter keystroke would bring me to the 4 dot loadscreen(this time yellow dots and not white).
Eventually after rebooting into recovery mode a few times, I fristratingly spammed arrow keys after not being able to do anything. What happened was me flashing inbetween the loadscreen and the Recovery Menu 3-4 times before landing on the recovery menu. After a few restarts, I no longer see the loadscreen in recovery menu.

I now try to use my menus to fix my filesystem. I can't because I'm in read-only mode.
I open root shell prompt and land at a screen that says:
Give root password for maintenance
(or type Control-D to continue):_

At this screen I attempt to login to root, but every keystroke resets the prompt returning:
Login incorrect.
Give root password for maintenance
(or type Control-D to continue):_

I can't login through this menu, so I google again. I try using ctrl alt F1, but I can't type anything in that menu.

I would try to run off of a CD, but my computer can't run CDs at this time. Any help is appreciated.

---

### Post by fr2632 on 2013-04-13
You can try to boot via usb. try this: [http://www.thelinuxguy.nl/tips-and-tricks/how-to-create-a-bootable-usb-stick-with-multisystem/](http://www.thelinuxguy.nl/tips-and-tricks/how-to-create-a-bootable-usb-stick-with-multisystem/)

---

### Post by claracc on 2013-04-13
Ubuntu 11.04 reached its end of life support on 28 October 2012. For this reason I think you cannot upgrade your version to the new one with software update manager.

I think you'll have to use live CD for 12.04 (I recommend it) or 12.10 in order to install the new ubuntu or if you cannot use CD-Rom try with the usb iso of the new release [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

