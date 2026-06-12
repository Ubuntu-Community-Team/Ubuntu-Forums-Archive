---
title: "How to force resolution in TEXT mode"
date: 2012-10-19
forum: General Help
---

### Post by jrandombob on 2012-10-19
Hi All,

    Not sure if this is the best forum for this question, mods, feel free to move it if you feel it is better elsewhere.

I'm currently building 12.04.1 LTS system based around a 7" touchscreen but I've run into an issue, the screen's native resolution is 800x480 (but it works fine at 800x600) but it's DDC data reports it will do 1024x768.

The framebuffer comes up in 1024x768 mode and it is very difficult to read the console at that resolution.

Basically I'm trying to force the kernel framebuffer back to 800x600 (or disable it all together and kick it back to pure text mode).

I've tried adding vga=771 to the kernel commandline by inserting it into the "GRUB_CMDLINE_LINUX_DEFAULT" variable in /etc/default/grub and running sudo update-grub, no dice (tried various different mode numbers).

I've also tried setting nofb and nomodeswitch the same way, no change.

I've set GRUB_GFXMODE=800x600 (which *does* set GRUB's resolution correctly) and GRUB_GFXPAYLOAD_LINUX=keep, that doesn't work either (as soon as grub launches the kernel it switches to 1024x768 )

I've also tried setting GRUB_GFXPAYLOAD_LINUX=text, that doesn't do it either.

I've also modified the scripts in /etc/grub.d to add "set gfxpayload=keep" and "set gfxpayload=text" neither made any difference (I made sure that there were no other "set gfxpayload" entries)

I either want my kernel framebuffer to be 800x600 or I want to disable the framebuffer all together and drop the kernel into text mode, how can I achieve this?

Thanks,

-J

---

### Post by jrandombob on 2012-10-25
Since nobody seems to be able to help here I suppose we switch to Plan B and rewrite the EDID EEPROM in the display so it tells the machine it'll only do 800x600... 

It's a pain but it'll also save me having to have this same fight with X later...

---

