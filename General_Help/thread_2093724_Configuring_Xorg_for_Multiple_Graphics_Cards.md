---
title: "Configuring Xorg for Multiple Graphics Cards"
date: 2012-12-11
forum: General Help
---

### Post by Kchymet on 2012-12-11
This may be a slight repost of my previous question ([http://ubuntuforums.org/showthread.php?t=2093087](http://ubuntuforums.org/showthread.php?t=2093087)), but my question is a bit different this time.

So as I mentioned before, I have 2 graphics cards: an ATI Radeon HD 5770 and an NVIDIA Geforce GTX 550Ti, connected to 3 monitors. The NVIDIA card has output going through 2 DVI ports, while the ATI card only has an HDMI output. My issue is that I can't get both cards to work at one.

Previously I thought this was because the devices had different drivers, but then realized that shouldn't be a problem, especially if X's configuration files still list both cards. Now I suspect X to just not be configured correctly. Now, after some searching it seems that
```
X -configure
``` is deprecated and should not be use, but then how should I go about configuring X?

As a final note, running xrandr only lists screen 0 (both the DVI monitors) and the connections from the nvidia card. My final goal would be to include the ATI's HDMI display on the same "screen", but configuring each to be a separate X screen would also be acceptable.

Also, I doubt that it matters, but the DVI outputs are 1680x1050 monitors and the HDMI output is a 720p TV.

---

### Post by TheFu on 2012-12-11
Interesting problem.

From what I've seen, ATI assumes it is the only video card(s) in the system, so when you tell it to initialize using the ATI utility, xorg gets overwritten.

Similarly, 
From what I've seen, nVidia assumes it is the only video card(s) in the  system, so when you tell it to initialize using the nVidia utility, xorg  gets overwritten.

So, I see 3 reboots involved.
# use only the ATI card - initialize xorg. Save that file somewhere.
# use only the nvidia card - initialize xorg. Save that file somewhere.
# Manually merge those saved files into the final /etc/X11/xorg.conf, carefully creatnig new stanzas for each display and card and for how you want the desktop extended (or not). I doubt you can get X to run across different cards - you'll be running 2 instances of X11 - 1 per card, if this even works.

Honestly, I'd go out an purchase the cheapest, driver compatible card for the vendor that you are happiest with. 100% ATI or 100% nVidia. Their drivers will recognize that setup and probably **do the right thing.**  For $60, all these issues can go away, perhaps less. I have an nvidia 430GT that handles dual outputs nicely. I think those cards are about $60 now.

If you do ever get the mixed card setup working - backup that X11 config file in like 10 different places so you never lose it again. While it isn't hard, getting all the details in a manually created X11 conf file correct is non-trivial.

Good luck!

---

### Post by dannyboy79 on 2012-12-11
i doubt xorg can load 2 different graphics modules in the same session, case in point, nouveau and nvidia drivers can't both be loaded so I don't an ati and an nvidia driver would load.

i just bought a nvidia geforce 8400 gs for 32.00 off newegg, that would be $64 total and you could run 4 displays. they have vga, dvi, and hdmi

---

### Post by Kchymet on 2012-12-11
> **TheFu said:**
> Interesting problem.

From what I've seen, ATI assumes it is the only video card(s) in the system, so when you tell it to initialize using the ATI utility, xorg gets overwritten.

Similarly, 
From what I've seen, nVidia assumes it is the only video card(s) in the  system, so when you tell it to initialize using the nVidia utility, xorg  gets overwritten.

So, I see 3 reboots involved.
# use only the ATI card - initialize xorg. Save that file somewhere.
# use only the nvidia card - initialize xorg. Save that file somewhere.
# Manually merge those saved files into the final /etc/X11/xorg.conf, carefully creatnig new stanzas for each display and card and for how you want the desktop extended (or not). I doubt you can get X to run across different cards - you'll be running 2 instances of X11 - 1 per card, if this even works.

Honestly, I'd go out an purchase the cheapest, driver compatible card for the vendor that you are happiest with. 100% ATI or 100% nVidia. Their drivers will recognize that setup and probably **do the right thing.**  For $60, all these issues can go away, perhaps less. I have an nvidia 430GT that handles dual outputs nicely. I think those cards are about $60 now.

If you do ever get the mixed card setup working - backup that X11 config file in like 10 different places so you never lose it again. While it isn't hard, getting all the details in a manually created X11 conf file correct is non-trivial.

Good luck!

Thanks, I'll try that. I'd like to avoid buying new cards as I have Windows as a dual-boot here for gaming and my current setup is perfect (you never have quite the same problems on Windows... That's part of why Linux is great though). Plus, I consider my time essentially value-less, so I'd rather spend days trying to get drivers to work than buy a new card :P I'll post back here if I find a solution.

---

