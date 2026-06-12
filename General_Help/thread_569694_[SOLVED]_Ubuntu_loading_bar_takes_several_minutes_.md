---
title: "[SOLVED] Ubuntu loading bar takes several minutes to move"
date: 2007-10-07
forum: General Help
---

### Post by kmg_12 on 2007-10-07
When the Ubuntu loading screen comes up the loading bar at the bottom does not move for bout 3 minutes. I can't find a solution anywhere for this.

Please help. I'm new to linux.

---

### Post by alex77 on 2007-10-07
when you boot up, press escape to enter the GRUB menu


press e
select the kernel line and press e again to edit it.
remove the words quiet and splash from the line
press ENTER
press b to boot

this will boot without the splash screen so that you can see what is taking so long when you are booting.

Post what you see, and hopefully someone will be able to help you.
Probably not me... I'm still a bit new to ubuntu too.

---

### Post by kmg_12 on 2007-10-07
I booted with quiet and splash removed and discovered where it is stalling. As I said I'm new to Linux so I don't know what this means.

ata2.00: udma/33
failed to recover some devices retrying in 5 seconds

It then retrys several times before moving on.
Another error i get is:

failed to set xfermode

If you need any more info let me no.


Any Suggestions?

---

### Post by alex77 on 2007-10-08
Ok, looks like its your CDROM drive thats causing you grief by not being recognized by the kernel

have a look at this thread, or search forums for: cdrom xfermode

[http://ubuntuforums.org/showthread.php?t=414002&highlight=cdrom+xfermode](http://ubuntuforums.org/showthread.php?t=414002&highlight=cdrom+xfermode)

What motherboard are you using?


some things that *may* help:
   boot with a cd in the drive
   set your boot order in bios to HDD first, then cd
   unplug your cdrom drive
   wait till a new kernel is available to upgrade to
   add irqpoll to the kernel line

---

### Post by kmg_12 on 2007-10-08
Thanks for your help. I followed the link and changed
 my cdrom for master to cable select and that seemed to solve the problem.

---

### Post by alex77 on 2007-10-09
Super. glad it's sorted.

---

