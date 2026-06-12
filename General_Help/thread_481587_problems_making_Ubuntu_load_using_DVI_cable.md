---
title: "problems making Ubuntu load using DVI cable"
date: 2007-06-22
forum: General Help
---

### Post by slaguth on 2007-06-22
I just built a computer, and dual booted both Windows XP and Ubuntu. My system specs are as follows:

AMD 64bit dual core processor
2 GB RAM
Nvidia 8800 GTS

I installed Widows XP first, then Ubuntu. I initially used a VGA monitor, and both systems seemed to work... and then I got a new monitor, and Ubuntu wouldn't seem to work with the DVI cable plugged in. After loading Grub and selecting Ubuntu, the screen just turned black and stayed that way. If I switched the DVI cable for a VGA cable and used a DVI/VGA converter to plug it into the computer, it worked fine.

I have updated to the driver to the newest Nvidia driver, and that helped but didn't solve the problem. And I am fairly sure that it isn't a hardware problem because it works fine under Windows.

I think I have come up with something of a workaround, but it is a little bit of a pain...
I can start the system with the DVI cable plugged in if I start in recovery mode, then I used the command line to start X11 processes with the command "telinit 2". I starts up Ubuntu as if I had started it normally, but it doesn't have a problem with the DVI cable.

I also resaved the Xconfig file using the nvidia-settings utility after I got Ubuntu to start normally. Although that helped for when I booted through recovery mode, it did nothing for booting normally.

I have absolutely no idea why this works. If anyone could help me get this thing working normally, I would appreciate it.

Thanks.

---

### Post by kidders on 2007-06-23
Hi there,

I had a similar problem with the same hardware. It seems to be due to a shortcoming in usplash that prevents it handling certain screen resolutions properly ... which is why you can boot successfully in recovery mode.

The simplest solution is probably to disable your bootsplash altogether. It's not quite as pretty, but it works perfectly. :-)

---

