---
title: "VGA/HDMI out isn't simultaneous"
date: 2012-10-16
forum: General Help
---

### Post by mgoben on 2012-10-16
**Ubuntu 12.04 with Nvidia Geforce 210:**

After multiple days of Googling and forum browsing I am defeated, I hate to ask a common question but I'm stuck. Please don't make me resort to a dual-boot windows install, I'm trying to never look back...

I have been trying to get my Nvidia GeForce 210 to mirror the display to my HDMI port on the tv, but it will only do one or the other. If I have both the vga monitor hooked up, and the HDMI port when I reboot the computer, the display only shows on the TV and not the monitor. In Nvidia settings I can't create another X screen, and it doesn't detect multiple displays, just the acer vga monitor. I see that others get this working, it is very frustrating not achieving the same.

I would love to get a mirrored or cloned display to my tv working so that I can stream video to it in the other room, please help!

---

### Post by mgoben on 2012-10-16
I believe that some xorg file editing may help solve the problem, but the only info I can find is about specific situations different from mine. Any pros out there?

---

### Post by pqwoerituytrueiwoq on 2012-10-16
try using dvi instead of vga

---

### Post by mgoben on 2012-10-17
I would give that a shot, but unfortunately my acer lcd monitor only has a VGA in port. The graphics card does have a dvi output in addition to the hdmi and vga, would using a converter be the same? I know it would defeat the purpose as far as the monitor goes but would it work to "trick" the graphics card? If you think it has a real chance at working I could go buy an adapter, I'd just hate to waste money if this can be accomplished through configuration instead.  I wish I could get this working on my own, but at this point I don't even know where to begin.

---

### Post by Grenage on 2012-10-17
It's been a while since I've tried to clone a display, and you can probably achieve what you want with xrandr, but...

There should be a twinview option for cloning the display; if you're not getting it within nvidia-settings, you can add them to xorg.conf directly.  I believe the command is along the lines of:

```
Option "TwinViewOrientation" "clone"
```

Which would be placed in the *screen* section of xorg.conf.

---

