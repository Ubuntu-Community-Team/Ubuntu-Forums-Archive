---
title: "Really need a fix :/"
date: 2008-03-12
forum: General Help
---

### Post by L815 on 2008-03-12
I have a vaio fz240e laptop that I bring everywhere to get work done. The problem is, the battery management is non-existent. Nor does the brightness of the screen dim when I'm using only a battery. This alone cut's a lot of the battery power.

I've tried xbacklight, which worked at one point, but now it doesn't, my battery life is low because there are no power options.
Are there any solutions???

Also, not as big of a problem, is there a fix for slowness when playing video + effects enabled?

I'm using Hardy alpha 6. Yes, the problems also exist with gusty.

---

### Post by Suparious on 2008-03-13
as long as your BIOS settings are enabling power management, you could try some packages. Did you search synaptic (or apt) for "laptop" or "battery"?

things like these may be helpful:

```

suparious@shaun:~$ apt-cache search laptop |grep power
gnome-power-manager - frontend for gnome-powermanager
laptop-mode-tools - Scripts to spin down hard drive and save power
powersaved - power management daemon
ubuntu-laptop-mode - Support for reducing hard drive power consumption
powertop - linux tool to find out what is using power on a laptop
```

regarding the video, check that you have 3D accelleration enabled. From a command line you could use "glxinfo". if you see things like "MESA", then you are not taking advantage of your graphics hardware 3D accelleration.

---

### Post by L815 on 2008-03-13
Thank you for the reply. I will give these a try and post the results :)

---

### Post by L815 on 2008-03-13
So installed a bunch of those power apps, none give me options like windows (low, powersave,high) mode, but if they improve the batterylife, that's all I really need for now. I'll see through these next few days if the life improves.

As for glxinfo, I do see MESA around. I'm pretty sure my card has 3Dacceleration, I just have to find out how to enable it. (intel gm965)

---

