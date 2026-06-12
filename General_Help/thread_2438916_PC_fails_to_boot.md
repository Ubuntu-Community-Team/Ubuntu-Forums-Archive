---
title: "PC fails to boot"
date: 2020-03-20
forum: General Help
---

### Post by satimis on 2020-03-20
Hi all,

Ubuntu 18.04

PC fails to boot
(I'm now working on a spare PC)

While I was fiddling around to solve VLC unable to play CD/VCD.  The screen blinked and I couldn't reboot PC.  Neither the Reset button worked, forcing me switching off the PC.

After switching on the PC again, I'm unable to start Ubuntu, finally dropping to a black screen after booting.

I'm able to start Recover Mode or drop to Root shell.

Please advise how to fix the problem.  Thanks in advance.

Regards
satimis

---

### Post by satimis on 2020-03-20
Performed following test;

Drop to root shell
Edit /etc/default/grub
change the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
as
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

# update-grub
# reboot

Now Ubuntu 18.04 can boot login page
After login the screen resolution is only 1024x764
Unknown display
I couldn't change the resolution

Any advice will be appreciated

Edit:
==
$ lspci | grep VGA```

08:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Picasso (rev c8)

```

$ xrandr```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768      76.00* 

```

satimis

---

### Post by satimis on 2020-03-20
Hi folk,

Problem solved.

It took me almost a day to figure out the problem.  It is the problem of the HDMI cable.

This computer is without graphic card.  The graphic comes from the CPU "AMD Ryzen 5 3400G with Radeon Vega Graphics 3700 MHz".  I wasted lot of time on the direction to find whether the problem coming from the CPU.

Finally I changed the display to an old 24" Samsung display, resolution 1920x1080.  My working display is DELL 25" display, resolution 2560x1440.

After changing back the line on /etc/default/grub from```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

```
to;
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
Ran
```

$ sudo update-grub

```
Reboot PC

Then I found the PC booting up to login screen.  After login I found the Samsung display detected with resolution 1920x1080.

Again I used the HDMI cable of Samsung display to connect the DELL display.  Now the PC is working without problem with DELL display detected, resolution 2560 x 1440.

That is the complete story.  I'll purchase a new HDMI cable later.

Regards
satimis

---

