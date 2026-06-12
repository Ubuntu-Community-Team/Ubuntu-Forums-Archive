---
title: "Startup splash screen gone after installing NVIDIA Driver."
date: 2015-07-12
forum: General Help
---

### Post by Ricial on 2015-07-12
**OS:** Xubtuntu 14.04 LTS
**VGA:** NVIDIA GeForce GT 520M
**DRIVER VERSION:** Version 331.113


Fast forward, I had installed the pending updates (Software Updater) and the proprietary driver (Additional Driver) from NVIDIA (Version 331.113) and after my laptop rebooted the splash screen (Xubuntu wallpaper with circling loading logo at the bottom) was gone.

The startup splash screen was then replaced by this NVIDIA logo/image

[IMG]http://i.imgur.com/HQO8IdA.gif[/IMG]


**NOTE:** I've found a lot of workaround information on how to solve this problem and perhaps bring back the nice looking startup splash screen. But my problem is I can't decide which one to follow since every solution is different from the other. I mean other suggested to edit the GRUB while some suggested installing some script via terminal. This confuses me because I'm new to Linux and I'm afraid that I may break something.

---

### Post by Dennis N on 2015-07-12
In the terminal, use the command:
```

sudo nvidia-xconfig --no-logo

```
[I]information source:
[http://ubuntuhandbook.org/index.php/2013/08/remove-nvidia-logo-from-ubuntu-startup-screen/](http://ubuntuhandbook.org/index.php/2013/08/remove-nvidia-logo-from-ubuntu-startup-screen/)
[/I]

---

### Post by Ricial on 2015-07-13
Will that command also bring back the old startup splash screen of Xubuntu?

I always end up having the same problem from all Linux distros based on Ubuntu that I have install. I got this similar issue on (Ubuntu w/ Unity, Xubuntu, Linux Mint w/ MATE and XFCE.

---

### Post by Ricial on 2015-07-18
Also, every time my laptop boots up it displays an "over current usb port" message.

---

### Post by pqwoerituytrueiwoq on 2015-07-19
is there anything in your usb ports? something is using too much electricity is what it means if they are empty blow them out if the message persist is is probably wrong
the only other thing it could possibly mean is there is some override in place that allows larger current flow than the USB port is specked for
something like a usb 3 HDD connected to a USB 2 port without a second port in use could do it
*USB 3 supports 0.9A while USB 2 supports 0.5A, a cable with 2 plugs going to a HDD allows you to use 2 USB ports for power in parallel so for example 0.5A+0.5A=1A

this is the guide i used way back when to fix the boot resolution
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)
here is a newer guide
[http://www.binarytides.com/ubuntu-fix-nvidia-graphics/]("http://www.binarytides.com/ubuntu-fix-nvidia-graphics/")
using my 1080p tv screen i end up with a large black border around my splash screen

---

