---
title: "Power settings GUI to extend battery life"
date: 2007-03-06
forum: General Help
---

### Post by FIONEX on 2007-03-06
Hey,

I was wondering if there's a GUI app that can modify CPU freq and monitor brightness for laptops with centrino chipsets.  I need to be able to extend the battery's life to 4 hours because that's what I get on windows.

---

### Post by 23meg on 2007-03-06
You can use the CPU Frequency Scaling Monitor GNOME panel applet to modify frequencies and governors. After issuing ```
sudo chmod +s /usr/bin/cpufreq-selector
```it will let you adjust the settings as well as monitor them.

---

### Post by FIONEX on 2007-03-07
Does that include dimming the screen.  Can I make profiles for certain settings so that I can change them on the fly?

BTW, I have an acer 2428 (2420 series with centrino chipset Pentium M).  Is there a specific app for it?

---

