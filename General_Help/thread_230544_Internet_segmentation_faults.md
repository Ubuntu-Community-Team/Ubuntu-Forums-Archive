---
title: "Internet segmentation faults"
date: 2006-08-06
forum: General Help
---

### Post by olliek on 2006-08-06
Hi
My internet connection keeps bombing out, causing firefox to crash.  If I run it from a terminal I get a "segmentation fault" and nothing else that could help me identify the problem.  Opera and Epiphany also crash, as does Frostwire.  I don't have any plugins installed so it isn't that.  XP has no problem and I installed Freespire last week and that didn't have any problems (apart from it won't run Compiz or Bluetooth yet!).  Please help as it's driving me maaaaaad!
My PC specs are:
Processor - AMD Athlon 64 3200 Processor
Memory - 1024MB DDR-400 RAM
Hard DiskHard Disk - 200GB Serial ATA Hard Disk
Graphics - ATI Radeon Xpress 200 128MB PCI Express Integrated Graphics
Monitor - 19" TFT Flat Panel Monitor

---

### Post by OffHand on 2006-08-06
Looks like your physical memory is having issues. Try to run memtest from the grub. 

[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

---

### Post by olliek on 2006-08-06
I don't think that memory is the problem because XP and Freespire both work OK.  I have just rebooted and gone in to recovery mode and have not had the problem in the last half hour of surfing so I think I have a conflict somewhere along the line.
I've got no idea where though, which is where I need help.

---

### Post by olliek on 2006-08-09
If I log on in recovery mode, I don't get any problems at all.  How can I pinpoint what program/driver is causing me problems?  In normal mode, firefox will crash every few minutes.  It might be when I click on a link but it also just dissappears when I'm reading a web page.  Frostwire crashes at any point between loading up and getting half way through a song, I haven't managed to download a full one yet.  What is the difference between Recovery mode and Normal login mode?

---

### Post by olliek on 2006-08-16
It looks like I'm talking to myself but I'm determined to work out what the problem is.  Can anybody tell me why, when I use recovery mode, I don't have any problems but I do in normal mode?
How can I pinpoint what the problem is?

---

### Post by olliek on 2006-08-30
Hi
I found the problem.  It is kind of memory related, so apologies to Offhand.  I found this on the memtest website:

"There have been numerous reports of errors with only tests 5 and 8 on Athlon systems. Often the memory works in a different system or the vendor insists that it is good. In these cases the memory is not necessarily bad but is not able to operate reliably at Athlon speeds. Sometimes more conservative memory timings on the motherboard will correct these errors."

So I turned the RAM speed down in my BIOS settings and the problem disappeared. I haven't noticed any difference in performance but I don't play games.  I have, however, got Compiz running and Google Earth and they seem ok.
Hope this helps someone, somewhere!

---

