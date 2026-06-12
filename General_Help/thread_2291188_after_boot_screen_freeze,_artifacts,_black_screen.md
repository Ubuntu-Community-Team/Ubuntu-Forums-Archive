---
title: "after boot screen freeze, artifacts, black screen"
date: 2015-08-18
forum: General Help
---

### Post by AlterFalter on 2015-08-18
Hello,

i have installed a 32 Bit Lubuntu 14.04.2 (now udated to 14.04.3) LTS on a Toshiba Laptop Satellite M30X-122 (here the details [http://www.toshiba.de/discontinued-products/satellite-m30x-122/](http://www.toshiba.de/discontinued-products/satellite-m30x-122/) there is a 30 GB HDD and 512 MB RAM installed ).
Every time the system boots up it ends in sometimes a black screen, a screen with black and white artifacts or in most cases the logon screen is displayed and freezes after some seconds (means it is not possible to enter something with the keybord or to klick on something; the mouse is still moveable).
I'm beginner in Linux and read a lot of things and tried them but the more i read and try the more i get confused as nothing seems to work.
Here is the output (if i have the luck to open a console after booting) of the video hardware detection:
```
lspci -nnk | grep "VGA\|'Kern'\|3D\|Display" -A2

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV350/M10 [Mobility Radeon 9600 PRO Turbo] [1002:4e50]
    Subsystem: Toshiba America Info Systems Device [1179:ff02]
    Kernel driver in use: radeon
```

Beside the fact that it is not exactly the video card that is installed in the laptop (Radeon Mobility 9700) it seems that the right driver "radeon" is used.

For the moment the only way how i can boot and login and use the os is to add manually the "nomodeset" bootoption into Grub2 during boot. But doing so the screen resolöution is not the best that is possible and all grafical things look little bit slow (opening windows or moving windows around on desktop).

I have read that in the current kernels the kernel itself is responsible for "communication" with the grafic device and sets the resolution and all the other "modes" of the device and not the X Server and nothing needs to be set in the X Server settings (like /etc/X11/xorg.conf).
But this "nomodeset" bootoption will tell the kernel to not be responsible for all the graphic device settings and gives control back to X Server.
So my questions are now:
do i need this "nomodeset" or is there any way to get the system run with this kernel mode? 
or do i need to set permanently the "nomodeset" bootoption and set up all the configurations in the X Server (etc/X11/xorg.conf)?
or do i need to set something in the XServer and in the Kernel but without haveing the "nomodeset" bootoption?

regards

---

