---
title: "Booting with nouvea drivers with Nvidia GTX 1650"
date: 2020-08-15
forum: General Help
---

### Post by Hewjr100 on 2020-08-15
I find that the default nouveau dirver works best with my Nvidia GTX 1650 gpu.  However when I boot or reboot I get a black screen and or freeze at boot.  I have added nouveau.modeset=0 at boot and login is fine.  Blacklisting nouveau in /etc/default/grub (nouveau.modeset=0) causes the same problem.  Even tried setting user to autologin, but same situation.  I would like to save nouveau.modeset=0 to boot menu, because I have to keep adding it at every boot, but I do not know how.  Any suggestions would help.

Henry

---

### Post by CelticWarrior on 2020-08-15
> [COLOR=#000000]I find that the default nouveau dirver works best with my Nvidia GTX 1650 gpu[/COLOR]
Surely not in this universe.

> [COLOR=#000000]However when I boot or reboot I get a black screen and or freeze at boot.[/COLOR]
Thaty's exactly because the open-source nouveau has poor support for your card. At the time of this writing it requires the latest Nvidia drivers - 450.xx - for best results.

> [COLOR=#000000] have added nouveau.modeset=0 at boot and login is fine. Blacklisting nouveau in /etc/default/grub (nouveau.modeset=0) causes the same problem.[/COLOR]
That or 'nomodeset' is the same. And any of this modes override all graphics drivers including nouveau, giving you only a very generic graphical mode that always works but is like driving a powerful car with a 7-speed DCT always in 1st gear. If you're happy with it we have to wonder why you have the Nvidia card? Any weak integrated GPU will do a much better job in anything.

> [COLOR=#000000]Even tried setting user to autologin, but same situation.[/COLOR]
Just DON'T. Autologin shouldn't be used, period. Please learn good practices that now are also the standard in Windows and that must mean something, don't you think? Besides, this has nothing to do with the graphics performance or the reported issues.

---

### Post by Hewjr100 on 2020-08-15
Just experimenting with autologin.  So that I can work with this problem, but autologin didn't work anyway.  Back to password login.

Henry

---

### Post by Hewjr100 on 2020-08-15
One thing I forgot, when using Nvidia proprietary driver, my fan is trying to get my laptop to Mars faster than the new Mars Rover.  Also lm-sensors only shows this and I fave a 6 core AMD R5 3000.

> sensors
BAT1-acpi-0
Adapter: ACPI interface
in0:           4.02 V  
curr1:         0.00 A  

acpitz-acpi-0
Adapter: ACPI interface
temp1:        +55.0°C  (crit = +115.0°C)

Henry

---

### Post by CelticWarrior on 2020-08-15
lm-sensors doesn't work properly with AMD Ryzen. This has nothing to do with the Nvidia Graphics card.

> [COLOR=#000000]when using Nvidia proprietary driver, my fan is trying to get my laptop to Mars faster than the new Mars Rover[/COLOR]
Increased fan activity should be expected because with proper drivers the card is actually working for things it was designed for and with the expected performance. That said, if the noise and fan rotation is excessive, it may need cleaning. And also UEFI updates tend to improve such things. Nothing of this is a reason not to use the proprietary drivers. As already commented, if you don't want or need the graphics card full potential, don't use it. It's that simple:

You can surely use a 233HP SUV [Changan CS75 Plus]("https://www.changan.com.cn/car/cs75plus/") for your daily commute but do you really need those 233HP for that? Maybe all you need is the 75HP small hatchback [Changan E-Star]("https://www.changan.com.cn/car/benben-E-Star/?navActive=6")...

---

### Post by Hewjr100 on 2020-08-15
Gotcha, this Laptop is lees than 30 days old, basically new.  But anyway even my old Laptop with GTX 1050 never made my fan run so fast and loud>  I thought the GTX 1650 would perform better.  Funny thing is that this only happens when running Gzdoom with classic DoomI and DoomII wads, have over 700 wads.

Henry

---

### Post by CelticWarrior on 2020-08-15
Even new laptops often need firmware updates. Our resident expert OldFred always mentions that tidbit in any "trying to install Ubuntu in X computer".

---

### Post by Hewjr100 on 2020-08-15
Using 450, woriking better, now Nvidia settings app working.  Probably because I was swithcing back and forth between drivers.  This was a fresh install.

Henry

---

### Post by Hewjr100 on 2020-08-15
All is good, thanks for your time and help.

Henry

---

