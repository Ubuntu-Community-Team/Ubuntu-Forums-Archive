---
title: "Dual monitor laggs"
date: 2018-11-26
forum: General Help
---

### Post by ladiqe on 2018-11-26
Hello guys, Im new into Ubuntu/Linux systems. I installed it becuase win10 is totall garbage ;)

But I have problem with dual monitor setup. I have 2 monitors, Acers, everything looks ok, I can log in, I can use whole Ubuntu system, but windows are laggy, when Im moving with them, they are laggy, stuttering or something like that. When I unpluged 1 monitor, everything works ok. Also when Im moving window inside 1 monitor, even 2nd is plugged in, there is no lag, but when I move window into 2nd monitor, there is lag.

My system:
OS: Ubuntu 18.10
CPU: Phenom II X6 1055T
GPU: GTX 460
Driver: Nvidia 390 - installed sudo apt-get install nvidia-390

Wayland is disabled

Thank you

---

### Post by logix2 on 2018-11-26
See if using Force Full COmposition Pipline in Nvidia Settings makes this better. THe option is in Nvidia Settings under X Server Display Configuration, after clicking Advanced - you should see "Force Full Composition Pipeline" there. If it works, the Arch Linux [wiki]("https://wiki.archlinux.org/index.php/NVIDIA/Troubleshooting#Avoid_screen_tearing") has a section on how to make this change permanent.

This might also help (from the same wiki linked above):

>  Multi monitor setups using different model monitors may have slightly different refresh rates. If vsync is enabled by the driver it will sync to only one of these refresh rates which can cause the appearance of screen tearing on incorrectly synced monitors. Select to sync the display device which is the primarily used monitor as others will not sync properly. This is configurable in ~/.nvidia-settings-rc as 0/XVideoSyncToDisplayID= or by installing nvidia-settings and using the graphical configuration options.

---

