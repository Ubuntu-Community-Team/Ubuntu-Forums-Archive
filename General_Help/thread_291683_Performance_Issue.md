---
title: "Performance Issue"
date: 2006-11-02
forum: General Help
---

### Post by perrymans on 2006-11-02
Hello all,

Running Edubuntu 6.06 on the kids computer, but it seems to be dragging a bit more than it probably should be.

CPU Speed: 1202 Mhz
RAM: 91MB out of 250MB
Swap: 109MB out of 996MB

I know the RAM isn't large, but it certainly isn't even close to being tasked.

The CPU usage in my Superkaramba monitor is idle at around 21% and jumps to 100% when I do anything, even closing a tab in Firefox.

I did upgrade the kernel to the K7 kernel because it is an Athlon processor.

These just seems too slow and sluggish for Linux on a 1.2Ghz with nothing running.

Any ideas on what could/ should be done?

Thanks in advance! Sean.

---

### Post by chriscando on 2006-11-02
Try using the program called 'top'. It runs in a terminal, just type top to start it ('q' to exit) and see if there is anything unusual taking up cpu. Maybe this is what Superkaramba does, im just not familiar with it.

---

### Post by perrymans on 2006-11-02
Thanks for the help.

It does look as though Xorg is the culprit.

It is ruinning at around 12 - 14% normally, but jumps to over 50% from just moving or resizing a window.

Do I need to recompile my install maybe?

The refresh on the graphics is pretty weak too, could it be the wrong video driver causing too much work by the CPU?

Thanks. Sean.

---

### Post by chriscando on 2006-11-02
That does seem high for Xorg. You might try changing the video driver, to something like 'vesa' in your xorg.conf file. Was is sluggish like this before the kernel upgrade?

---

