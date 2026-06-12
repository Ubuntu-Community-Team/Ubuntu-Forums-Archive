---
title: "Crazy X11 prob, please help"
date: 2007-02-16
forum: General Help
---

### Post by soulfury on 2007-02-16
Allllright.  Let me start by saying I've googled and read debian, ubuntu, general X11 forums for 4 days now with no luck.  I cant get anything other than 640x480 to display.

Intel 945 chipset video card, trying to connect to a sony HDTV over the laptops DVI out.  Ubuntu 6.06.  Xorg.conf file has a modeline for the tv I created using the clock, vsync, and hsync params returned by by X's EDID fuctions.

X knows the TV's res is 1920x540 (1080i, since its interlaced its 2 540s to equal 1080), it shows you that much in the xorg.0.log.  I've defined the mode 1920x540 in xorg.conf in the 16 and 24 bit depth sections, as well has patched mode 4c and 5c to 1920x540 with 915resolution.  It doesn't seem to matter what I do, xorg.0.log doesnt show 1920x540 for modes 4c or 5c when its showing you all the modes and their various values.  5c is (0x0), which makes me think the card's video bios is not passing the mode to X?  X log always says 'not using mode 1920x540 (no mode by this name)'.  I've tried 1920x1080 as well as other resolutions I know the TV supports.  

915resolution thinks the patch is good, cuz after I do 915resolution 4c 1920 540, 915resolution -l shows mode 4c 1920x540.

Anyone got any ideas?

I've tried IgnoreEDID 1 in xorg.conf, as well as the linearalloc param.

---

### Post by veloce on 2007-02-17
in xorg.conf, try referring to the mode as "4c" rather than "1920x540".  It may be just the name that isn't getting through.

---

### Post by krangnes on 2007-05-18
Have you got it to work? I've got the same problem with my macbook

---

