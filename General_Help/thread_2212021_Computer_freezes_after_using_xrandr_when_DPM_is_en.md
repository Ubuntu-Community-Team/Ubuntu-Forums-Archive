---
title: "Computer freezes after using xrandr when DPM is enabled"
date: 2014-03-18
forum: General Help
---

### Post by omgtallmonster on 2014-03-18
I had been having problems recently with my graphics card overheating since dist-upgrading to 13.10 (sometimes reaching 120+ degrees C according to lm-sensors). I have not had any problems with overheating in Windows.

I added "radeon.dpm=1" to the kernel parameters in accordance with this wiki page: [https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later](https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later)

Enabling this option seems to solve my overheating problem. However, now whenever I use xrandr or arandr to reconfigure my displays (my 2 monitors initially start mirrored), the entire computer freezes a couple of seconds later. The X process goes up to 133-200% CPU usage before htop stops updating.

The exact randr command I'm running is: ```
xrandr --output DVI-0 --left-of DVI-1
```

I'm running 13.10 on a 64-bit machine. My graphics card is a Radeon HD 4770, and I'm using the open-source radeon drivers.

Does anyone have any ideas why xrandr would cause my system to freeze up? Is there any workarounds for this? Alternatively, are there any ways of making my screens not start mirrored without using xrandr?

---

