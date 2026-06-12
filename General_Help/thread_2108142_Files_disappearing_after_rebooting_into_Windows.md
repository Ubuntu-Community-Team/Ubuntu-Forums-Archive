---
title: "Files disappearing after rebooting into Windows"
date: 2013-01-23
forum: General Help
---

### Post by PinkFloyd102489 on 2013-01-23
I've noticed lately that some files are disappearing when rebooting into Windows from Linux. I have a partition formatted as exFAT that I use to store files that I need in both Linux and Windows. I can create a file in Linux, reboot into Windows, check the partition, and it's gone.

Is it possible that Linux isn't flushing the cache to disk for whatever reason when shutting down? Or is there a different problem?

For the record, when shutting down, I issue a "sudo shutdown -hP now".

---

### Post by AstroLlama on 2013-01-23
Windows "instant on" feature is just like "hibernate". Did windows go into hibernate when you logged off? if so any changes written to the disk will be undone after you reboot into windows as the disk reverts to the pre-hibernate state. If you want to write to the windows partition from Ubuntu you will have to completely shutdown the machine, not put it into hibernate.

---

### Post by PinkFloyd102489 on 2013-01-23
> **AstroLlama said:**
> Windows "instant on" feature is just like "hibernate". Did windows go into hibernate when you logged off? if so any changes written to the disk will be undone after you reboot into windows as the disk reverts to the pre-hibernate state. If you want to write to the windows partition from Ubuntu you will have to completely shutdown the machine, not put it into hibernate.

Crap you're right. Going to disable hibernate right now. It's caused me to lose too many important files.

---

### Post by AstroLlama on 2013-01-23
I also have a dual boot and was having the same problem, so I recognized yours right away! I didn't disable hibernate, as it can be useful but i followed directions like these to make a "shutdown tile" for when i shutdown windows and know i'll have to transfer files. actually i rarely use windows these days-- but the shutdown tile could be helpful in any case! :)
[http://www.micromart.co.uk/pc/windows-8/150/how-create-windows-8-shutdown-and-restart-tile](http://www.micromart.co.uk/pc/windows-8/150/how-create-windows-8-shutdown-and-restart-tile)

---

