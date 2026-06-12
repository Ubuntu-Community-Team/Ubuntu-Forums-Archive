---
title: "TTY 1- 6 screen doesn't fit  monitor, scrolls off the bottom"
date: 2006-11-06
forum: General Help
---

### Post by Aglystas on 2006-11-06
Hi everyone,
    I'm a new convert to ubuntu and have gotten most things up and running with a litle work, but I can't seem to find any information on the this particular topic.  Whenever I log into terminal mode (ctrl-alt-[F1-F6])  the text isn't entirely on the screen, the left and bottom edges are cut off.  I can only see the end of the prompt (probably the last 3 or 4 characters and the '$' symbol) and anything that I type. And then there's about 2 full lines at the bottom of the terminal that I can't ever see when entering information.  This is of course annoying because I can't be sure that what I want to enter is correct until the lines have scrolled up into the veiwing area.  I previously used Breezy and this wasn't happening until I did a fresh install of dapper.  Also GNOME desktop is correctly sized, so I can only assume it isn't the X window system.  I have a nvidia 6600 GT and a sceptre widescreen monitor.

---

### Post by Najand on 2006-11-06
I think it is a BIOS issue... You may need to setup your monitor automatically/manually.

---

### Post by chrisccoulson on 2006-11-06
Just a stab in the dark, but maybe you need to try setting a widescreen console resolution by passing 'vga=0x360' as a kernel boot option. This should give you 1280x800 resolution AFAIK.

You can do this at boot time, by pressing [ESC] as GRUB loads, to get to the GRUB menu. With the default option highlighted, press [E] to edit the current option. Scroll down to the line beginning 'kernel /boot/vmlinuz....', press [E] again, and then append 'vga=0x360' to the end of this line. Press [ENTER], and then press [B] to boot with this option.

If this works, add the option permanently in /boot/grub/menu.lst.

---

### Post by Aglystas on 2006-11-07
I took a look at the bios settings, and couldn't locate any settings for the monitor.  I tried the second method, going into the grub settings and attempted to add the command to the end of te line, but received an error, stating that mode wasn't an option.  So I instead typed in 'scan' and found a list of 7 line modes.  I choose the 80 lines by 40 lines mode, let the machine finish booting up, and everything worked fine in Console Mode.  I needed to adjust the monitor itself by about a centimeter, but I see all the text now.  I haven't restarted the machine, but I imagine I can just make the change perminent as you stated above later on. Thanks for the help.

---

