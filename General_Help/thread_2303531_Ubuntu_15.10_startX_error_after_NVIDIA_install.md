---
title: "Ubuntu 15.10 startX error after NVIDIA install"
date: 2015-11-19
forum: General Help
---

### Post by bwanaaa on 2015-11-19
Wily worked fine when installed to SSD. Added NVIDIA proprietary driver. Worked fine. (pc has NVIDIA 780Ti)
Transferred SSD to a different pc with NVIDIA GTX 285 (much older video card)
Booting to Ubuntu results in a lot of screen flashing (startX trying to start and then failing)
Login screen appears but user credentials do nothing.
Going to terminal (ctrl-alt F1) and trying sudo startX gives:
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
error setting MTRR (base = 0xf5000000, size = 0x00e00000, type = 1) Invalid argument (22)
xinit: connection to Xserver lost

The log file says:
adding GPU devices
...
LoadModule: "glx"
NVIDIA GLX Module 352.55
...
NVIDIA (0) The NVIDIA GeForce GTX 285 GPU installed in this system is supported through the NVIDIA 340.xx Legacy Drivers
The 352.55 NVIDIA driver will be ignored. Continuing probe..


So obviously I need to downgrade the driver. 
Is there a way for ubuntu to have several drivers and pick the right one?
Is there a way to fall back to the nouveau driver when the NVIDIA driver fails as in this case?
Is there a way to 'safe boot' into the nouveau driver and downgrade the nvidia driver? Or do I have to go back to the PC where I installed the NVIDIA drivers and downgrade from there?

---

### Post by Vladlenin5000 on 2015-11-19
You can uninstall the current drivers:
```
sudo apt-get purge nvidia*
```
Reboot and you should be running with nouveau. Then install the recommended nvidia driver directly from System settings > Software Properties > Additional drivers thus ensuring you have the version which has been tested for your specific graphics.

---

### Post by QDR06VV9 on 2015-11-19
> **bwanaaa said:**
> 
So obviously I need to downgrade the driver. 
Is there a way for ubuntu to have several drivers and pick the right one?
Is there a way to fall back to the nouveau driver when the NVIDIA driver fails as in this case?
Is there a way to 'safe boot' into the nouveau driver and downgrade the nvidia driver? Or do I have to go back to the PC where I installed the NVIDIA drivers and downgrade from there?
1. Yes Down Grade the Driver
```
sudo apt-get remove nvidia*
```
2.This with out installing a new driver will default back to nouveau after a reboot.
3.There is no way for one system to use mulitible video drivers at once IE: 340 && 355
4.After removeing the driver and a reboot just reinstall the driver you need for that card.
```
sudo apt-get install nvidia-340
``` 
Kind Regards
Sorry Vladlenin5000 you were faster got caught up with a converstion.

---

### Post by grahammechanical on 2015-11-19
> Is there a way for ubuntu to have several drivers and pick the right one?

It is called Additional Drivers and we find it in System Settings>Software & Updates. It will offer us 5 relevant drivers for a graphic adapter. This is why is it always best to change video drivers using Additional Drivers and not by downloading a driver from the manufacturers web site.

In my case support of my Nvidia GT220 has been dropped from the latest Nvidia drivers. So, Additional Drivers does not offer me the latest Nvidia drivers. Only the newest Nvidia drivers that support my graphic adapter. With Additional Drivers we always get the right one. It is designed that way.

In Software & Updates we can tick the box "Proprietary drivers for devices (Restricted) and we will get updates to the proprietary video driver. 

Regards.

---

### Post by bwanaaa on 2015-11-19
thank you all for your replies. is there a difference between:
sudo apt-get purge nvidia*
and
sudo apt-get remove nvidia*
?

too bad there isnt a comparable tool to msconfig in linux where I can set boot options/services with granularity and easily. boot up manager is a crude attempt but it only lists a few services like cgmanager, uuidd, rsyslog,thermald,kerneloops,cgproxy,whoopsie,speech-dispatcher,irqbalance,bluetooth,lightdm,cups,saned,etc

Simple choices like:
boot into safe mode
boot into safe mode with networking
etc
would make troubleshooting bootup issues easier.

---

### Post by QDR06VV9 on 2015-11-19
> **bwanaaa said:**
> thank you all for your replies. is there a difference between:
sudo apt-get purge nvidia*
and
sudo apt-get remove nvidia*?



[COLOR=#111111][FONT=Ubuntu]As the man apt-get page says:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**remove** - Packages installed are removed (Does NOT include configuration files)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**purge** - Purge is identical to remove except that packages are removed and purged. Purge meaning that any configuration files are deleted too.[/FONT][/COLOR]
Ethier way should be okay, But just to be sure nothing is left behind to foul up, I would use the purge argument.

> [COLOR=#000000]Simple choices like:[/COLOR]
[COLOR=#000000]boot into safe mode[/COLOR]
[COLOR=#000000]boot into safe mode with networking[/COLOR]
[COLOR=#000000]etc[/COLOR]
[COLOR=#000000]would make troubleshooting bootup issues easier.[/COLOR]
In a Perfect World?
That would be nice, But Lets not forget how much we get with ubuntu with no cost to us, And A lot hard work from the Developers.
I'm saying that as much for myself as anyone else.(No Offense meant)

---

