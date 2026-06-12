---
title: "Bootup Issues:  Kernel Panic?  That doesn't sound good"
date: 2007-01-29
forum: General Help
---

### Post by healthpellets on 2007-01-29
Alrighty, well here's the deal.  I turned on my computer, and now it doesn't work.  After I select Ubuntu at the GRUB menu, this is message I get:

Starting Up...
[17179574.052000] RAMDISK:  ran out of compressed data
[17179574.052000] invalid compressed format (err=1)
[17179574.052000] Kernel panic - not syncing:  VFS: Unable to mount root fs on unknown-block(0,0)
[17179574.052000]

That's it...I think it's important to note that I haven't upgraded anything or changed any settings or anything since the last time it worked (i.e. this morning).  It just stopped working.  So, if you have any tips, suggestions, or thoughts, I'd love to hear em.  

Thanks.

---

### Post by mysticrider92 on 2007-01-29
I would kind of guess that this is a Grub configuration problem. Try opening the Grub boot menu and press the button to edit the commands before booting ("e" I think), and make sure the boot drive is defined properly. Other than that, I don't know what the problem would be.

---

