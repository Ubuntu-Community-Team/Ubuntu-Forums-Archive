---
title: "display in grayscale for energy savings"
date: 2013-03-11
forum: General Help
---

### Post by pacman401 on 2013-03-11
Is display in grayscale (directly from graphic card) cuses less energy usage ?
If yes then how to enable it ?

Lubuntu 12.04
IBM/Lenovo T60
Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller

---

### Post by Cheesemill on 2013-03-11
No.

Decreasing the brightness of your screen will reduce energy usage though.

---

### Post by tgalati4 on 2013-03-11
I have a Thinkpad T43p and using powertop, you can measure actual watts used by various  subsystems.  I found CPU was #1 in power usage followed by Screen.  Only turning down brightness had an effect of 1-3 watts less usage out of 22 watts total draw.  Dark sceen or light screen or different colors didn't matter, only the backlight level.  LCD's only use 2.2 volts so there is not much to switch on and off.  The backlight uses 90Volts for the florescent ballast, so it's quite a bit more power. 

I recompiled my kernel to enable undervolting with PHCtool and I was able to save an additional 4-5 watts of power, which was an improvement that got close to WinXP runtimes on battery--4 hours versus 2.5 hours without power tweaks.

---

### Post by pacman401 on 2013-03-15
U are talking about power savings in LCD by reducing brightness , but I was thinking about reducing power usage in graphic crad by using only grayscale (8bit instead of 16 or 32) less bits to process less energy  am I wrong ?

---

### Post by dcstar on 2013-03-15
> **pacman401 said:**
> U are talking about power savings in LCD by reducing brightness , but I was thinking about reducing power usage in graphic crad by using only grayscale (8bit instead of 16 or 32) less bits to process less energy  **am I wrong** ?

Yes. In the same way that using different coloured ink on a newspaper does not make it lighter.

---

