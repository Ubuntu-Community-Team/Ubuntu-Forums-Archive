---
title: "Slow download on usb from camera"
date: 2005-10-30
forum: General Help
---

### Post by ardvark on 2005-10-30
Today I tried to download some pictures from my digital camera connected to a USB  port. The camera was recognized and a program came up to download the pictures. When that process started I noticed that it was extremely slow. It appears to be downloading data in around 60k blocks and waiting1 to 2 seconds between blocks. So, instead of 30 seconds to get 60+ pictures, it's more like 30 minutes. I looked around and didn't see this problem come up, also I never tried this when I had Warty loaded.

---

### Post by munkymonkjr on 2005-10-30
to be honest i am clueless. your best bet is to double check how your USB was configured. maybe it was the program. Did you use gtkam? or just Nautilus? sometimes maybe the program is to blame

---

### Post by ardvark on 2005-10-30
The first program that starts up automatically to download pictures is gThumb, but using the file manager has the same problem. The only other device I have on a USB is the printer. But this type of problem is probably not going to show up there. I just wonder if I ought to send this to a bug report?

---

### Post by mrquick on 2005-11-15
I have also had this problem and I have a solution.  Now mind you my problem may be different from yours, but I had this working in warty then had the extremely slow USB in Breezy and this is the problem and how I remedied it.  For some reason my usb controller shares an IRQ with my ethernet controller (a pci card).  No matter what I did I could never get the two to work together, I believe this is a 2.6 kernel issue as it was never a problem with the 2.4 version.  The way I got around it in Warty was to add this to the kernel line of my /boot/grub/menu.lst file: noapic noioapic nolapic.  This returned the slow usb port to normal transfer speed.  You might not have it as bad as me noapic may be all you need to do if this is your problem.  Anyway the weird thing is, in 2.6.12 (breezy) this is no longer a problem, just an annoyance... if you don't add the noapic stuff to kernel initialization, it will still work, albeit slowly.

---

### Post by kruz on 2005-11-15
im not 100% sure
but doesnt usb have DMA support
or need it for faster computing

or possibly its running at 1.1 speeds not 2.0 because of some missing packages
just suggestions im not 100% sure

---

