---
title: "Brightness Issues"
date: 2013-06-18
forum: General Help
---

### Post by skarme on 2013-06-18
Quick story and problem: 

I had this issue on my laptop ever since replacing its screen. In Windows 8 the brightness level would either be the highest or go to the lowest using function keys. The bar would move but the brightness changed only at the highest and lowest level. I then installed Ubuntu as a dual boot for my school project that needed special C++ libraries and they were much easier to install on Ubuntu than on Windows using Synaptic Package manager (was a previous user of Ubuntu...since Ubuntu 8.10). The problem persisted with Ubuntu as well and I thought it was a hardware issue since I myself changed my laptop screen I might have messed up (that's what I thought).

However one fine day I happen to do some google search for a fix for the same in Ubuntu; I came across a link with detailed instructions for power management, etc and to my surprise it worked. I for the first time in months could adjust my screen brightness to different levels. Now to the problem. I recently formatted my computer and installed Linux Mint this time. Again, same issue. I thought I could fix it using the same Ubuntu commands (as Linux Mint is Ubuntu based) and did the usual google search (had not saved the Ubuntu link). I sadly could not find the link and I'm still struggling to find and fix it. 

For your information, I've tried editing grub with the "quiet splash" thing and a few other stuff. It does not work. On changing that what happened is that my laptop on Mint start-up remains brightest as opposed to the dimmest without editing the grub. The bar on function key and brightness adjust also does not move. If I quickly press brightness up or down it sometimes changes brightness, but again either too low or too high. I can however change brightness through the terminal to various levels using xrandr but obviously it is tedious and does not feel right. If only I had saved the link. It had a couple of instructions and talked about power saving. I think it enabled multiple brightness levels than normal. 

Any help would be greatly appreciated. This issue is annoying me

---

### Post by pqwoerituytrueiwoq on 2013-06-19
Any of these jog your memory for what you did?
```
acpi_osi=
acpi_backlight=vendor
acpi_osi='!Windows 2012'
acpi_osi=Linux
```

---

### Post by skarme on 2013-06-19
This is what I know I did
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=#000000][FONT=Ubuntu Mono]acpi_backlight=vendor[/FONT][/COLOR]"
and I did try acpi_osi='!Windows 2012' forthe next line GRUB_CMDLINE_LINUX

---

### Post by skarme on 2013-06-21
Anyone has some knowledge to fix this issue? I've always got help on here...

---

