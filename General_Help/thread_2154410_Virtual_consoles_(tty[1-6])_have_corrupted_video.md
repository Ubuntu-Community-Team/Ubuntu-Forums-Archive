---
title: "Virtual consoles (tty[1-6]) have corrupted video"
date: 2013-06-14
forum: General Help
---

### Post by seebarn on 2013-06-14
Fresh install of xubuntu 13.04 on a desktop machine with Nvidia GeForce 6200A video card hooked (via VGA cable) to an LG 50" plasma display with native resolution of 1360x768.  nvidia-current drivers installed.  Custom xorg.conf with appropriate modeline for that display.  X works beautifully.  However, none of the virtual consoles work properly - the video is corrupted on them, and they don't update at all as the console is used.  The consoles are accepting input just fine - I've tried blindly logging on and issuing commands (such as sudo shutdown -r now) and that works fine, but there's no output.

I've tried tampering in /etc/default/grub and have found a few things but no solution:

1) If I set a graphics mode for GRUB, e.g. GRUB_GFXMODE=1024x768, that mode works fine for GRUB.  If I keep that mode e.g. GRUB_GFXPAYLOAD_LINUX=keep the virtual consoles will have corrupted video.  Specifically setting a resolution such as GRUB_GRXPAYLOAD_LINUX=1024x768 has the same effect.  I've tested a variety of the modes listed by GRUB's VBEINFO command, they all work in GRUB and they're all corrupt in the virtual consoles.  Note that the monitor's native resolution, 1360x768 is not one of the modes VBEINFO lists, that's why I'm not using it in GRUB.

2) If I set GRUB to text mode, e.g. GRUB_TERMINAL=console, that mode works fine for GRUB.  GRUB_GFXPAYLOAD_LINUX=text (or keep, with GRUB set to console) gives me a black screen with a cursor for each virtual console, but nothing typed is ever displayed there (although, as before, the console does respond to input, it just doesn't display anything).

Also, there is no graphic splash screen when booting, despite boot options "quiet splash" being set.  Just a succession of black or dark grey screens until X starts up and displays the login prompt.

I have also tried setting a specific vga mode, e.g. vga=788 or vga=normal on the boot options, but this has similar effect to setting GRUB_GRXPAYLOAD_LINUX .

Any ideas?!?

---

### Post by seebarn on 2013-06-14
I've found a workaround - I switched from the Nvidia proprietary driver to the Nouveau driver and that has corrected the issue.  All the ttys are working fine, still in the 1024x768 mode that is specified in /etc/default/grub.  

There was a little fallout - Nouveau seems to interpret the MODELINE in xorg.conf ever so slightly different, so the left edge of the screen was hidden (tweaked it and that's working OK now).  

Also, the background screen at the Xubuntu login and the desktop background once I've logged in are foobar - it looks like it's incorrectly loading those up at 4:3 aspect ratio and then tiling them, instead of stretching them out.  And it's not saving changes to the desktop background setting (well, actually, it seems to be saving them but not using them when it loads the initial background).  So something odd is going on under Nouveau that wasn't happening under Nvidia, but at least the consoles are working.

For kicks, I tried loading the earlier nvidia-173 drivers instead of the current nvidia-304 but they screw up the consoles as well.

---

