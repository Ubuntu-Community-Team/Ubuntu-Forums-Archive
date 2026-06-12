---
title: "Problems Sleeping and Hibernating"
date: 2008-06-19
forum: General Help
---

### Post by Zoasterboy on 2008-06-19
I have a Toshiba Satellite laptop, 2GB RAM, 2GHZ Processor, Hardy.

I was once able to sleep and hibernate the laptop easily, but suddenly it refuses to work. When turning the computer back on from sleep, a blank screen comes up and the computer refuses to respond untill forced to shut down and start again.

When coming out of hibernation, the computer freezes on the Ubuntu load screen.

Does anyone know of a fix for this, or are there any Logs I can provide that might help the debugging process?

Thanks! :)

---

### Post by ar-jar on 2008-06-20
Hi,
I have a similar issue on my new AMD Phenom 9750 Quad-Core 2.4 GHz, Gigabyte GA-MA770-DS3 motherboard,and Gigabyte GeForce 8600GT graphics board. When returning from hibernation, I get two different behaviors depending on the graphics driver:
- With NVidia native driver I get a blank (pinkish) screen where there actually is a login textbox but you can only find it by moving the cursor around (since everything is pinkish).
- With the default OSS driver the system hangs with an enlarged and downshifted Ubunto logo.
(I happen to have an old Toshiba SatellitePro 4600 on which hibernation and standby work excellent with the 8.04 so this seems to be hardware dependent.)
-Arto

---

### Post by Zoasterboy on 2008-06-20
I found a similar post with some good info:

[http://ubuntuforums.org/showthread.php?t=786311&highlight=sleep+hibernate&page=5](http://ubuntuforums.org/showthread.php?t=786311&highlight=sleep+hibernate&page=5)

[QUOTE=danwood76]The version 2.6.24-19 kernel has the bug fixed.
You may need to enable the hardy proposed repository to get it, or just wait until it gets released into the main repos.[/QUOTE]

---

### Post by ar-jar on 2008-07-06
Hi, thanks. I seem to have the 19 version of the kernel installed now (synaptics tells me that I have *both* the 16.30 and the 19.34 installed - a lot that I still don't understand about Linux :-)). An hibernate started to work a week ago or so. Must test stand-by too...
/Arto

---

### Post by ar-jar on 2008-07-06
Stand-by (suspend) still doesn't work here. The computer shuts off allright but won't even output a video signal after having been switched on again.
/Arto

---

### Post by Zoasterboy on 2008-07-07
Both stand-by and hibernate work for me with the kernal update.

The old kernel stays on the system, and a new entry is added to the boot list for the new kernel. You can run ubuntu on the old and new kernels, but the new default option should be the newest kernel, so I'm not sure why it still isnt working for you.

I guess the update didnt fix all problems.

---

