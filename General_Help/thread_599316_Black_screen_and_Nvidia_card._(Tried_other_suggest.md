---
title: "Black screen and Nvidia card. (Tried other suggestions.)"
date: 2007-11-01
forum: General Help
---

### Post by mivo on 2007-11-01
Well, I spent the past day and today trying to install Gutsy on a brand-new desktop with an Nvidia 8800GTS card. Installing from the Live CD works (after I figured out that the kernel option *irqpoll* fixes another problem that 7.10 had with my hardware), but after booting I always get a black screen.

So, I went into the Grub menu, hit e for edit, removed *quiet,* added *nosplash, irqpoll, nolapic* and hit b for boot (should this restart the system?), and I still get the black screen.Alt+F1 does not work, space does nothing, either. So, I'm pretty much out of ideas. I seem to be unable to get a shell other than Grub's.

I should probably mention that Fedora Core 8 RC2 worked absolutely flawless and had no issues with either the video card or the rest of the hardware, and installed in about half the time. The issue here is 7.10. The irony is that my old system had Compiz-issues with 7.10 because of the ATI card, and the new system has issues because I bought an Nvidia card because of the previous issues. ;)

This is the 64bit version, by the way.

---

### Post by mivo on 2007-11-01
Booted into the Live CD, mounted the disk and edited /boot/grub/menu.lst, adding the kernel options mentioned before. Same result, I still get the black screen.

---

### Post by ericartman on 2007-11-01
Well I probably can't help you but we are running the same video card I have a 640mg8800GTS and I get all the bells and whistles from Compiz. The only difference that I see is I did a clean install from a 32 bit version of Gutsy download. Didn't upgrade and used the 32bit by mistake but all went well for me. Prior to doing this I did back up my home and evolution so the "New" install was easy. BTW the install correctly identified my video card and monitor(22 inch LCD) I did no adjustment even for my resolution. I wish you well and good luck.

Cart

---

### Post by Fire_Chief on 2007-11-01
Do you see anything after the GRUB boot menu at all?

Can you boot into failsafe mode (uses the VESA driver)?

If you can't see anything in failsafe mode, then I'd be suspect of your grub boot options in the menu.lst file. You can boot from the live CD and mount the /boot partition to view the file ( located at /boot/grub/menu.lst ).

---

