---
title: "Additional GPU drivers for Nvidia on Lubuntu."
date: 2016-02-05
forum: General Help
---

### Post by arthur24 on 2016-02-05
I tried Lubuntu recently.

I have a GTX 750 TI graphics card.
A 3570K intel cpu and 8gb gskill ram.

Rebooting with a installed proprietary driver installed through the software & updates window usually results in booting errors and problems with the screen display. This forced me to boot into failsafe mode and even forced me to completely reinstall Lubuntu earlier as I got stuck into booting the system all together.

I did look around, and tried installing proprietary drivers with terminal commands. I tried that based on instructions given by others, to others. In any case, my installation is now completely clean. It has only Lubuntu on it, no packages or other software is installed other then OS updates. Just to ensure I go from A to Z.

It seems that specific to each case the actual installation procedure may differ. Like I said, in my case I have a completely clean install of Lubuntu. 
I’m not at all sure what exact steps are required to correctly install the gpu drivers. And what I try, fails.

Under software & updates > additional drivers I have the open source X.org drivers.
And there are options for > 352,63 and 340.96 drivers with or without updates.

First of all, the open source drivers cause massive fps issues. A game written on a unity kernel runs with 1 fps per second at best (with X.org). And when I move a window over the desktop, it seems the displayed fps is not 60fps as it should be on my 60hz monitor. 
I would expect the computer to perform 60fps on the desktop in all cases, even with a graphics driver written by a vegetable.
I never had such performance issues on Ubuntu with (X.org).
So am I missing some basic software dependencies that I don’t know about? That I would need to install on Lubuntu that Ubuntu already has? (besides the gpu drivers)

When I load the 352.63 and 340.96 drivers any video game that I try to launch will not launch. 
A window may pop up but the game doesn’t start and the window closes.

I don’t really understand why there even is a additional drivers tab within the software & updates window. I have never been able to succesfully install proprietary drivers by clicking checkboxes in this window on both amd and nvidia, Ubuntu or Lubuntu. Maybe others have more luck.

---

### Post by buzzingrobot on 2016-02-05
I have a 750ti.  It boots to a black screen with the open source driver.

The 352.63 driver works well here.  The 340 drivers do not. I'm not a gamer so I can't comment about FPS rates, etc.

The Nvidia card needs to be active before Additional Drivers can detect it and offer proprietary drivers for installation. The kernel will default on boot to the open source Nouveau driver if an Nvidia card is active.  To avoid the black screen here, I interrupt the boot process, add the "nomodeset" parameter, which enables a visible, but degraded display.  I then run Additional Drivers, install the proprietary driver, and reboot.
 
Additional Drivers can take several minutes, or more, to complete. Hitting a slow repo server takes more time.  More is going on than dropping a driver file into a directory.

---

### Post by arthur24 on 2016-02-05
Yes! Great...

Adding nomodeset installed the drivers nicely, and the games run perfect. I read about nomodeset being a necessity for installation with the Live CD, good to know the same fix is needed for the drivers when booting.

---

