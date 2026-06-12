---
title: "Display Issues after install"
date: 2008-02-18
forum: General Help
---

### Post by tshearman on 2008-02-18
After cruising the forums for a while to figure out how to actually boot to Ubuntu, now once I boot to it the screen blanks out.

System Specs:
Intel Dual Core 2.6GHz
NVIDIA 8800GTS
2 gig Ram
17" HYUNDAI Imagequest LCD Monitor 

Also, dual booting between Vista on HD1 (SATA) and Ubuntu on HD2 (SATA).
Everything installed fine; I had no probems with the regular install from LIVE CD.

It appears that it wants to boot; I see "Kernel Live" and something else in the bottom of the screen before the display goes blank.

How do I install ENVY if I cant see anything?

Thanks! 

Toby

---

### Post by MoLE on 2008-02-27
The approach I would take is to boot into the 'rescue mode' from the grub boot menu (immediately after the BIOS messages).  You will then end up at a command prompt with root privileges. 

Then execute the following command.

```

sudo dpgk-reconfigure xserver-xorg

```

Follow the prompts.  If you're not sure about the correct response then go with the defaults.  I would suggest using the vesa driver (rather than the nvidia or nv driver), as this is more likely to give you a GUI so you can work on the problem from there (particularly in terms of accessing the restricted driver manager).

A blank screen could be due to a video card driver issue, or the horizontal and vertical sync values for the monitor may be incorrectly detected.

After doing this and rebooting, if you still don't have a GUI, then boot off a livecd and post your xorg.conf file here as an attachment.

---

