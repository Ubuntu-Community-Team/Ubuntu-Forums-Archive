---
title: "Nvidia Problems"
date: 2007-11-28
forum: General Help
---

### Post by djesse50 on 2007-11-28
I recently upgraded from 6 to 7 and am having problems with the infamous nvidia-glx drivers. When I was running 6, all I had to do was activate the restricted driver, and everything worked.

Now, when I active the restricted driver (nvidia-glx or nvidia-glxnew) the computer boots into safe graphics mode, and I cannot set my graphics to anything higher than 800x640 (or whatever it is). When not running the restricted drivers, my screen resolution is normal, but graphics are clunky, and things like scrolling and video rendering are off. Any help?

---

### Post by nick_h on 2007-11-28
What video card are you using?

Type:
```
lspci
```
to find out if you don't know.

---

### Post by -grubby on 2007-11-28
have you tried editing your settings by pressing ALT-F2 and typing

```
gksudo nvidia-settings
```

---

### Post by djesse50 on 2007-11-29
When I typed in the first suggestion, this is what I get:
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0c.0 PCI bridge: nVidia Corporation nForce2 PCI Bridge (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)


Will try the other later.

---

### Post by nick_h on 2007-11-29
I think you need the nvidia-glx driver. You can check on the [nvidia site](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9639/README/README.txt) - look in Appendix A.  This is a list of supported products for the 1.0.-9639 driver.  If you type:
```
lspci -n
```
it will give you the PCI Device ID which may help selecting the driver.

Gutsy nvidia-glx is version 1.0.-9639, but you always have the option of downloading a copy from the nvidia site and installing it.

Have you looked to see if you get any errors in your /var/log/Xorg.0.log file?

The nvidia-settings suggestion is also very easy to try.

---

### Post by PmDematagoda on 2007-11-29
Did you try removing the Nvidia drivers and reinstalling them again? That could solve your problem.

---

### Post by LauraSakura on 2007-11-29
Yours appears very similar to my computer. To get mine to work, I had to completely remove all nvidia drivers and then use the program ENVY to compile/install the nvidia binary drivers for me. It came up as the new legacy driver. For me, the restricted drivers thing did not work for my specific computer/card. Envy walks you through everything, I'm pretty sure it is in the repositories

---

### Post by nick_h on 2007-11-29
I don't think Envy is available in the repositories but you can get it [here](http://albertomilone.com/nvidia_scripts1.html).

Alternatively, downloading the driver from the nvidia site and installing it is quite easy.

---

### Post by djesse50 on 2007-11-29
I installed using Envy, and it works fine. Thanks!

---

