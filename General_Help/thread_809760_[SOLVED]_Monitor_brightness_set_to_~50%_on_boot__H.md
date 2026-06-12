---
title: "[SOLVED] Monitor brightness set to ~50% on boot:  HP dv6500 with Hardy Heron"
date: 2008-05-27
forum: General Help
---

### Post by ladr0n on 2008-05-27
I have an HP dv6500 laptop running Ubuntu 8.04 64 bit. About halfway through booting Ubuntu, my monitor goes to about 50% brightness (i.e. painfully dim).  I've noticed that it happens right after the NVidia driver is loaded.  The obvious work around is to bump the brightness up once Gnome is up and running, so this is only an annoyance, but I've gotten tired of beating around the bush, so to speak. 

This was not an issue with Gutsy (32 bit), and I noticed it the first time I booted after I upgraded to Hardy.  The kernel upgrade yesterday didn't fix it.  It happens regardless of whether the laptop is on AC or battery power.

I have disabled everything in the Gnome Power Management dialog that would dim the display for any reason, and that didn't affect this behavior.  It happens regardless of how the brightness was set when I shut down (unless the brightness is below 50%, in which case it just stays at the lower level).  

I'm using the nVidia Corporation GeForce 8400M GS video card with the proprietary nVidia driver (just ask if there's more information you need).

Could anyone point me in the right direction?

---

### Post by EXCiD3 on 2008-05-27
Interesting problem. I can't really think of what would be causing that to reset every time up. Have you changed the brightness settings in nvidia-settings at all?

I saw this little tidbit: [http://ubuntuforums.org/archive/index.php/t-311751.html](http://ubuntuforums.org/archive/index.php/t-311751.html)

---

### Post by ladr0n on 2008-05-27
I didn't have nvidia-settings installed before.  I just installed it and followed the instructions in that other thread, but unfortunately it seems that it can only control the lcd brightness, not the backlight (which is problem.  forgot to specify that.)  I'll reboot now and see if it helped though.
--edit--
Yeah, on reboot it still reset the backlight brightness.  xgamma also only touches the lcd brightness, not the backlight.

---

### Post by EXCiD3 on 2008-05-27
i cant remember if it was that post or not but you can changed the backlight brightness with "gconf-editor" its one of the options in there somewhere i forget now...

---

### Post by ladr0n on 2008-05-27
/apps/gnome-power-manager/backlight looked like it should have done the trick.  I basically set all the options to 100% brightness no matter what.  I rebooted, and it still reset my backlight brightness in the same place.
Do the gconf settings effect the whole system or just gnome?  I would assume that gnome-power-manager doesn't actually start doing anything until gnome starts, which would be after the brightness change occurs... I'll keep looking.

--edit--

AHA!  I found something.  The value of /sys/class/backlight/acpi_video1/brightness controls the back light power.  I have a simple script that will set this to 10 (the desired value)
```

#!/bin/bash/
echo "10" >> /sys/class/backlight/acpi_video1/brightness

```
Running that during the boot sequence works.  It's still just a work around (the display dims and then brightens back up again right before X launches) but at least it works.  Thanks for your help!  If anyone can think of a reason the display was dimming up in the first place, please let me know.  At this point, I'm just curious.  *shrug*

---

### Post by EXCiD3 on 2008-05-27
Yeah, now that i think about it, the gconf thing wouldn't be causing it because its after the problem happens. Glad you found a fix! I'll have to make sure i mention it in the next revision of my tutorial! You might check launchpad.net to see if there are any bugs posted about it.

---

