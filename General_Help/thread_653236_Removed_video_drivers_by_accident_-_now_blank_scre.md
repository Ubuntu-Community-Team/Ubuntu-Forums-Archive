---
title: "Removed video drivers by accident - now blank screen after boot splash"
date: 2007-12-29
forum: General Help
---

### Post by WaySensei on 2007-12-29
I am running Gutsy on a first-gen Macbook Pro. I installed Envy in order to easily install the latest ATI Mobility graphics driver so that I would be able to suspend to RAM. This all proceeded fine. Now comes where it goes south. To see what would happen, I enabled the restricted ATI driver, rebooted, then disabled it, and again, rebooted. After disabling the restricted driver, I received a message notifying me of package uninstallation (of what I assumed were my video drivers). Now, after starting Ubuntu, the boot splash screen will load, and then be followed by a blank screen with a blinking cursor. Obviously, I am a n00b. 
From some other tips on these forums, I pressed ESC during boot to access recovery mode, and typed ```
dpkg-reconfigure xserver-xorg
``` and proceeded through the on-screen instructions, and rebooted when finished. Now, instead of just a blinking cursor, I have 3 or 4 flashes of color after the boot screen, and then, the blinking cursor returns.
I would be extremely grateful if someone could offer a fix.

---

### Post by Craigus on 2007-12-29
Try:

> sudo dpkg-reconfigure -phigh xserver-xorg

instead.

---

### Post by WaySensei on 2007-12-29
I did as you suggested, typing ```
sudo dpkg-reconfigure -phigh xserver-xorg 
```and selecting VESA, but still no luck. The blinking cursor is endless. I would be very welcome to other suggestions.

---

### Post by WaySensei on 2007-12-29
Please help...I would like to avoid reformatting if possible.

---

### Post by Craigus on 2007-12-29
Try removing / renaming /etc/X11/xorg.conf and let X start in bulletproof mode - does that work?

> sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.renamed

---

### Post by WaySensei on 2007-12-29
Unfortunately, no, that didn't fix it :( 

Should I just f it and reformat?

---

### Post by Craigus on 2007-12-29
It might be the quickest solution. I assume there's no data you need to keep on the partitions that will be reformatted ...

---

### Post by WaySensei on 2007-12-30
If I was not to go through the reformatting route, which I would prefer not to, how would I solve this issue? Running dpkg-reconfigure xserver-xorg just seems to reconfigure my xorg.conf, so is there something I could manually add to the xorg.conf to allow myself to log into the X session?

---

### Post by overdrank on 2007-12-30
> **WaySensei said:**
> If I was not to go through the reformatting route, which I would prefer not to, how would I solve this issue? Running dpkg-reconfigure xserver-xorg just seems to reconfigure my xorg.conf, so is there something I could manually add to the xorg.conf to allow myself to log into the X session?

Hi and are you able to boot into recovery mode and use the command startx?

---

### Post by WaySensei on 2007-12-30
Overdrank, thank you for the tip. I did as you suggested, and I am getting the following errors:

1. VESA: No valid modes
2. Screens found, but none have a usable configuration. 

What I did prior to running startx, was: 
```
dpkg-reconfigure -phigh xserver-xorg
```

and selected VESA for the display, and checked all the available resolutions that my display supports. 

Everyone's help thus far is much appreciated.

---

### Post by overdrank on 2007-12-30
> **WaySensei said:**
> Overdrank, thank you for the tip. I did as you suggested, and I am getting the following errors:

1. VESA: No valid modes
2. Screens found, but none have a usable configuration. 

What I did prior to running startx, was: 
```
dpkg-reconfigure -phigh xserver-xorg
```

and selected VESA for the display, and checked all the available resolutions that my display supports. 

Everyone's help thus far is much appreciated.

Ok form the recovery mode you can try and install 
```
apt-get install xorg-driver-fglrx
apt-get install xserver-xorg-video-ati
``` I did not include sudo because it is not needed in recovery mode. Then try and reconfigure with the command ```
dpkg-reconfigure -phigh xserver-xorg
``` That command will configure your driver and may let you choose the resolution. Then use the command starx.  I hope this helps.

---

### Post by WaySensei on 2007-12-30
After doing apt-get install xorg-driver-fglrx, I get the error: unable to fetch. I tried the same command when directly connected to my modem, with the same error. I assume this is due to a failure to connect to the internet? Pardon my newbie question.

---

