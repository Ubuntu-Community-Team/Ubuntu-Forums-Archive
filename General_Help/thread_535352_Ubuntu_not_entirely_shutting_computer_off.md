---
title: "Ubuntu not entirely shutting computer off"
date: 2007-08-26
forum: General Help
---

### Post by Rippy on 2007-08-26
Sometimes when I shut it down, it does everything except physically shutting down the PC. So the monitor isn't receiving input anymore, but the computer is still on.

And if it helps, this seems to have started after installind and using kubuntu-desktop.

Any help is appreciated, thanks.

---

### Post by sumguy231 on 2007-08-26
If you have an older computer*, try using these instructions to load Ubuntu with the "acpi=force" boot option:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Even if you don't get it working, remember that by that point it is safe to turn it off since everything has been stopped and all the filesystems have been unmounted.

*Or even if you don't, I guess.

---

### Post by fragos on 2007-08-26
My PC shuts down but still powers the USB.  I use the power strip switch to completely power down.  There also seems to be a relationship with DCHP.  If I don't totally switch off with the power strip, DCHP will use the last IP data collected.

---

