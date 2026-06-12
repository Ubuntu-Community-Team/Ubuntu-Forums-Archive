---
title: "Black boot screen &amp; freeze"
date: 2008-02-14
forum: General Help
---

### Post by LucidTaZ on 2008-02-14
Okay, first of all: I can't see my boot screen since I installed a new NVidia GeForce 8600GTS. My screen just goes blank and shows the orange blinking light that also shows when the monitor is in standby mode. I have read [http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075) and modified the resolution to several of which I am certain my monitor supports. Still no boot screen.

Until recently, this wasn't a problem. It would just boot and get into Ubuntu. But yesterday I installed 2GB of extra ram. I had 2x 1GB Kingston ram and I now have 4x 1GB Kingston ram. All PC-5300, 667MHz. Now it freezes during bootup and I cannot see why because my screen is black. I've given it over an hour to boot but it wouldn't continue.

I can boot into safe mode. :) Any suggestions?

My specs:
Processor: AMD64 X2 5600+ 2.8GHz
Memory: 4x Kingston 1GB PC-5300 667HMz DDR2
Operating System: Ubuntu 64 7.10 Gutsy
Motherboard: Asus M2A-VM HDMI
Graphics: Nvidia GeForce 8600GTS, 256MB ram
Monitor: Hansol 910A (CRT, most commonly used resolution by me is 1280x1024)

---

### Post by Crafty Kisses on 2008-02-14
> **LucidTaZ said:**
> Okay, first of all: I can't see my boot screen since I installed a new NVidia GeForce 8600GTS. My screen just goes blank and shows the orange blinking light that also shows when the monitor is in standby mode. I have read [http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075) and modified the resolution to several of which I am certain my monitor supports. Still no boot screen.

Until recently, this wasn't a problem. It would just boot and get into Ubuntu. But yesterday I installed 2GB of extra ram. I had 2x 1GB Kingston ram and I now have 4x 1GB Kingston ram. All PC-5300, 667MHz. Now it freezes during bootup and I cannot see why because my screen is black. I've given it over an hour to boot but it wouldn't continue.

I can boot into safe mode. :) Any suggestions?

My specs:
Processor: AMD64 X2 5600+ 2.8GHz
Memory: 4x Kingston 1GB PC-5300 667HMz DDR2
Operating System: Ubuntu 64 7.10 Gutsy
Motherboard: Asus M2A-VM HDMI
Graphics: Nvidia GeForce 8600GTS, 256MB ram
Monitor: Hansol 910A (CRT, most commonly used resolution by me is 1280x1024)

Hmmm, did you use the "Restricted Drivers Manager" when installing your drivers?

---

### Post by Crafty Kisses on 2008-02-14
You might also wanna reconfigure your X server, do the following:
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions the best you can, good luck.

---

### Post by LucidTaZ on 2008-02-14
_First question:_
Yes, I used the Restriced Drivers Manager to install my graphics driver.

_Second question:_
I used the dpkg-reconfigure xserver-xorg and selected the "nvidia" driver. All results still the same.

After that, I selected the "nv" driver. I still don't see a boot screen, but eventually it comes to a weird-looking deformed and strangely colored login screen. From there I can login and the screen returns to non-weird looking.

Though now I can't use the nvidia-settings anymore, probably because I don't use the "nvidia" driver.

[add]
In the Restriced Drivers Manager, it shows that the nvidia driver is not in use.

---

### Post by spyckotic on 2008-02-14
I wish you the best of luck in your adventure in getting that card working.  I have a 8600 GTS and have been unsuccessful in getting it working correctly with the "nvidia" drivers.  "nv" are fine however.  I have the same black screen/lockup when starting X.

- refer to this for even more people suffering from this..... with no solution
[http://ubuntuforums.org/showthread.php?t=615215&highlight=nvidia+broke](http://ubuntuforums.org/showthread.php?t=615215&highlight=nvidia+broke)

---

### Post by LucidTaZ on 2008-02-15
Well, I had it working perfectly before the RAM upgrade. With the "nvidia" driver. Everything worked like a breeze except for the black boot screen. But after the RAM upgrade suddenly it stopped working. O_o

Works fine in Windows btw.

---

### Post by LucidTaZ on 2008-03-10
I still didn't get this to work. Perhaps someone has a suggestion? :)

---

### Post by LucidTaZ on 2008-03-19
Does anyone know? I can successfully install the latest NVidia drivers from the website, but since I have 4GB of RAM, it won't start up. And I don't know what the problem is cause my screen is black.

---

### Post by mk1w86 on 2008-03-19
The problem of the black boot screen is probably because the resolution is set too high for your monitor.  The boot screen is configured separately because it does not use Xorg to display.

Edit the upsplash (Program that displays the boot splash) configuration file (you have to be root or use sudo) /etc/usplash.conf and change it to your desired resolution for the boot screen.

You then have to update your initramdisk so the new configuration file is used at boot. (May take a few moments)
Run

update-initramfs -u 
(as root)

or 

sudo update-initramfs -u
(as your normal user)

---

### Post by LucidTaZ on 2008-03-19
Hello mk1w86,

I followed your steps and set my resolution to 640x480. Then updated my initramdisk. Didn't work, still the same black screen. :(

(The original resolution in the file was 1280x1024, which I know my monitor can handle)

[add]
I just removed the splash screen so I could see what's going on at startup. I just see a lot of regular startup-text flashing by on my screen, and after that the screen turns black. I think it's at the time it tries to start X.

---

