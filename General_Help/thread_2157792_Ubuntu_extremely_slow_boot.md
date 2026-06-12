---
title: "Ubuntu extremely slow boot"
date: 2013-06-26
forum: General Help
---

### Post by erik1001 on 2013-06-26
Hello everybody.
I have fresh ubuntu 13.04 installation and it is extremely slow after I enter my password on login screen. 
Boot time from grub menu to lightdm login screen takes about 30 seconds and it's ok, but time between entering the password and finally usable desktop is up to 2 minutes, which is not normal. At first I thought I am running too many compiz plugins/extensions/services, but even on fresh install it was incredibly slow. After looking in Xorg.log, I can see that `(II) intel(0): Modeline "1366x768"x0.0 ...` is repeating several times. What does it mean and why it is running multiple times? Thanks in advance.
```

......................................
[    25.720] (II) XKB: generating xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[    28.766] (II) intel(0): EDID vendor "SEC", prod id 16978
[    28.766] (II) intel(0): Printing DDC gathered Modelines:
[    28.766] (II) intel(0): Modeline "1366x768"x0.0   74.80  1366 1414 1446 1578  768 770 775 790 -hsync -vsync (47.4 kHz eP)
[    31.704] (II) intel(0): EDID vendor "SEC", prod id 16978
[    31.704] (II) intel(0): Printing DDC gathered Modelines:
[    31.704] (II) intel(0): Modeline "1366x768"x0.0   74.80  1366 1414 1446 1578  768 770 775 790 -hsync -vsync (47.4 kHz eP)
[    36.976] (II) config/udev: removing device A4Tech RF USB Mouse
[    36.980] (II) evdev: A4Tech RF USB Mouse: Close
[    36.980] (II) UnloadModule: "evdev"
[    41.712] (II) XKB: reuse xkmfile /var/lib/xkb/server-E2C02DD8FA0CF39D142CC10BC3BCF64C11753BD4.xkm
[    42.763] (II) intel(0): EDID vendor "SEC", prod id 16978
[    42.763] (II) intel(0): Printing DDC gathered Modelines:
[    42.763] (II) intel(0): Modeline "1366x768"x0.0   74.80  1366 1414 1446 1578  768 770 775 790 -hsync -vsync (47.4 kHz eP)
[    44.086] (II) intel(0): EDID vendor "SEC", prod id 16978
[    44.086] (II) intel(0): Printing DDC gathered Modelines:
[    44.086] (II) intel(0): Modeline "1366x768"x0.0   74.80  1366 1414 1446 1578  768 770 775 790 -hsync -vsync (47.4 kHz eP)
[    52.868] (II) intel(0): EDID vendor "SEC", prod id 16978
[    52.868] (II) intel(0): Printing DDC gathered Modelines:
[    52.868] (II) intel(0): Modeline "1366x768"x0.0   74.80  1366 1414 1446 1578  768 770 775 790 -hsync -vsync (47.4 kHz eP)
[    54.623] (II) intel(0): EDID vendor "SEC", prod id 16978
[    54.623] (II) intel(0): Printing DDC gathered Modelines:
[    54.623] (II) intel(0): Modeline "1366x768"x0.0   74.80  1366 1414 1446 1578  768 770 775 790 -hsync -vsync (47.4 kHz eP)
[    70.770] (II) intel(0): EDID vendor "SEC", prod id 16978
[    70.770] (II) intel(0): Printing DDC gathered Modelines:
[    70.770] (II) intel(0): Modeline "1366x768"x0.0   74.80  1366 1414 1446 1578  768 770 775 790 -hsync -vsync (47.4 kHz eP)
[   136.199] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6758B387F241FF62B974FC1726CACE7F4C76634.xkm

```

---

### Post by sanderj on 2013-06-26
... on which hardware: CPU, RAM, ...

---

### Post by erik1001 on 2013-06-26
I thought it's software fault, not hardware, except slow HDD (I do not own SSD). Anyway, I don't think it causes '[COLOR=#000000](II) intel(0): Modeline "1366x768"x0.0 ...' [/COLOR]multiple times.

Ubuntu 13.04 64bit
2 * 4 GB DDR3
Intel Core i7-3632QM
Intel Ivybridge Mobile

---

### Post by grahammechanical on 2013-06-26
Your monitor is a SEC is it not? The xserver gets the monitor settings from the monitor and not from some script that lists the settings. This is why we do not need to set the monitor resolution and frequency when we install Ubuntu. Read about the Extended Display Identification Data (EDID) here

[http://en.wikipedia.org/wiki/Extended_display_identification_data](http://en.wikipedia.org/wiki/Extended_display_identification_data)

I guess what we are seeing when the log says modeline is the optimum setting for the monitor and several alternatives, I would not think that the problem rests with the Xserver because it has handed over to the video driver by the time the lightdm log in screen has loaded. Why it repeats, I do not know.

The strange bit is that it happens on a fresh install. I experience a similar delay but I am using Saucy Salamander and things like that happen with the development branch. 

Have you experimented with different video drivers?

[http://en.wikipedia.org/wiki/Extended_display_identification_data](http://en.wikipedia.org/wiki/Extended_display_identification_data)

Regards.

---

