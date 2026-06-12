---
title: "Video, login, usb install boot, dvd FAIL"
date: 2016-11-21
forum: General Help
---

### Post by Mark_in_Hollywood on 2016-11-21
Nvidia 6510SE in-built into motherboard cannot be set to nvidia-340, even though Settings/Drivers can find it.  With nvidia-340 installed, no login possible, only infinite login loop. Purging nvidia*, OS reverts to 640x480, but until this weekend, could run in 1280x1040.

Today, I tried to do a re-install of 16.04 and LiveUSB will not boot, even though BIOS can and at boot time F-11 brings up thumb drive to boot from. Selecting persistent (Unetbootin made) drive falls back to SATA (regular boot drive) and gives 640x480 res. 

Even the DVD drive is dead. 

On "regular" boot, screen resolution if 640x480 and Settings/Displays has no options. 

This an Athlon X2 620 4 core 64bit CPU. It used to have no problem booting from a LiveUSB drive. True since 12.04LTS+.

HELP!

---

### Post by irongolem0982 on 2016-11-22
Do you have a graphics card installed or just the integrated 6150? 

IF you have a graphics card: Make sure the bios is set to ONLY use the pci card and NOT the integrated, check the ports on the back too and make sure you are plugged into the graphics card.

once you have made sure that the bios settings are correct and that the cord is plugged into the right port try reinstalling. 

I have a working 14.04 install on [this motherboard]("http://support.hp.com/us-en/product/Compaq-Presario-CQ5000-Desktop-PC-series/4162245/model/4210061/document/c01701270/") with the 6150 that I use for a time clock station. might be worth a try to reinstall an older OS?


You mentioned unetbootin and not being able to boot to from the live usb. Try making the usb from another port or another computer, for more help have a look [here]("https://help.ubuntu.com/community/Installation/FromUSBStick").



Good Luck!!!

---

### Post by mörgæs on 2016-11-24
I assume that we are talking of Nvidia 6150 and not 6510.

If so then I suggest a fresh install of X/Lubuntu in which closed-source drivers are selected during installation (not after a reboot).

---

