---
title: "Allocate more memory to Video"
date: 2008-04-17
forum: General Help
---

### Post by Djalmahal on 2008-04-17
Hi,

I'm going to install an extra 1 GB Ram(on top of 1 GB existing) to my laptop running Ubuntu 7.10, and I have an Intel 945 Chipset with integrated graphic card.  Graphic performance has been fine but I wonder if it makes sense and id it's possible to allocate more memory to the graphics, maybe via xorg.conf or such. 

How do I find out how much memeory is used at this point for video?

THanks
Andreas

---

### Post by angry_johnnie on 2008-04-17
Looking at all the options that are given when reconfiguring xserver-xorg, it looks like you can allocate some of that memory to your video card.   I haven't done it, though (not enough ram).

---

### Post by Wim Sturkenboom on 2008-04-17
Have a look in the BIOS, there might be something there. I had an old  Dell with i810 which standard allocated 1MB; could change it to 4MB somewhere in the BIOS.

---

### Post by ryanhaigh on 2008-04-17
The memory allocation setting is generally found in the bios. If you change it there you won't need to modify xorg.conf unless you have already specified memory below what you allocated in the bios.

If there is no modifiable setting in the bios I don't think (although I could be wrong) that setting the paramater in xorg.conf will override the systems setting.

---

### Post by Djalmahal on 2008-04-17
Si,

I can't find any option to change the allocated video memory in the BIOS, so, i guess that it, nothing to do, as nobody though that changing xorg.cong would make any difference..

If anybody knows otherwise....

Thanks
Andreas

---

### Post by ryanhaigh on 2008-04-19
You could always just try adding the option although I don't know how you would confirm that it works other than perhaps checking the logs for x under /var/log. If it doesn't work you won't have lost much. Also you could check the manpage for your graphics driver, for example I use the mga driver in xorg.conf so using man mga gives me info about the available options.

---

