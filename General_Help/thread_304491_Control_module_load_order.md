---
title: "Control module load order?"
date: 2006-11-21
forum: General Help
---

### Post by celloandy on 2006-11-21
I've just gotten a new Macbook, and have been playing with getting the Synaptics driver working under X.  After patching and compile a shiny, new kernel, it seems to work, but only if the appletouch kernel module is loaded before the usbhid module.  Unfortunately, even if I put them in that order in /etc/modules, usbhid seems to get loaded first, so X fails to start, and I have to drop to shell, unload usbhid, load appletouch, and load usbhid again (all in one line, of course, because unloading usbhid makes the keyboard stop working).  How can I force the modules to load in the proper order?

Thanks,
Andrew

---

### Post by celloandy on 2006-11-22
Is this not the right forum for this question?  If not, might someone suggest a better one?

Andrew

---

### Post by barbex on 2006-12-14
I would also be very interested in a way to force a certain module to load before another one. I've been searching high and low for this but all I find are vage pointers to initRD and start scripts.
Can someone please enlight us?

---

### Post by cyberdork33 on 2007-07-16
I saw here someone suggesting a method.
[http://www.jasonparekh.com/?page_id=9](http://www.jasonparekh.com/?page_id=9)
(Scroll to Trackpad / Touchpad Section)

---

### Post by barbex on 2007-07-16
I found a solution for my problem recently. Apparently the order in which the modules  are written in "etc/modules" is already the load order but udev keeps shuffling them around. 
Now the "good" solution would be udev rules (very confusing for a newb!), the easy solution is to block udev from grabbing the modules by blacklisting them. Just append them to modprobe.d/blacklist and the modules will get loaded in the order of etc/modules.
Problem solved.

---

