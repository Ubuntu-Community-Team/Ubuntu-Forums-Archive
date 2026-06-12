---
title: "Framebuffer problems"
date: 2007-09-23
forum: General Help
---

### Post by chimerical_brio on 2007-09-23
I'm trying to set up a text-based partition on my computer, just for fun, and I've heard mention of framebuffer as a way of viewing photos and videos from the command line. So I tried the kernel argument in GRUB vga=xxx, but there's a problem: I'm trying to use a screen with a resolution of 1680x1050. The setting vga=0x314 works great except that the first character is cut almost completely off; anything above that, like vga=0x317, makes my screen go black and my monitor tells me that basically, it can't display anything. That's also what happens when the Ubuntu splash screen should be showing in normal Ubuntu, but it always works itself out when X starts.

I'm also very unsure about my video card. I'm running my computer off of a rather crummy no-name second hand motherboard that has a built-in video card, and I can't find any specs for it.

Any ideas on how I can make this work? Thanks a lot.

---

### Post by kerry_s on 2007-09-23
on boot vesa drivers are used, vesa don't go that high, i believe 1024x768 is the top, anything above that is trouble.
try
 vga=791

---

### Post by chimerical_brio on 2007-09-23
Hmm...well, I tried vga=791, but it didn't work. I got the same message about how the monitor was "Not in optimum mode, recommended mode 1680 x 1050 60 Hz." The manual tells me that that means that it's either giving more than 70 hz or "exceeds SXGA." I do know that when I configured X for this monitor, I used the vesa driver. Any ideas? Or is this a waste of time to try to figure out? Does framebuffer for viewing images on the commandline work even without setting vga in GRUB?

---

