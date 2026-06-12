---
title: "Stuck in BIOS After Attempt to Uninstall Win From Dual Boot"
date: 2016-12-27
forum: General Help
---

### Post by blueviolet2 on 2016-12-27
Hello all,

I'm mortified to be asking for help for this; it was sheer stupidity that caused it. 

Having little skill, I bumblingly (but oh so delusionally confident at the time)  tried to follow online instructions to uninstall Win10 from my dual boot system on my desktop.
I got Ubuntu three weeks ago and really wanted to get rid of Win10 which I always detested.

I installed OS UNINSTALLER, and followed a few prompts, it said something went awry (cannot recall what it said) and referenced BIOS, so I went to BIOS, tried to disable secure boot, did a few other things (mind you this is like a monkey doing surgery) and now I cannot leave BIOS. It's stuck, will not boot, will not shut down. I shut it down via the power button on the tower.

I'm pretty sure I'm well out of my depth and shall have to seek help from the local Linux folks, but until I can do that, is there ANYthing I can do to fix this?

Thanks in advance,
No Fool Like an Old Fool

---

### Post by oldfred on 2016-12-27
Power switch is last thing to try if in UBuntu. But I sometime have to use it.
Note order of S letter (sync) is not always consistent with phase but works either way. 
 Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

Best to have UEFI secure boot off, but UEFI on, or CSM off. Some systems say to have CSM on, but still let you select UEFI boot and do not work well with UEFI only on. Most seem to want CSM/BIOS/Legacy mode off.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

    Be sure to boot in UEFI boot mode, if system is UEFI.
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by blueviolet2 on 2016-12-28
Thank you for that! I tried, however, and no result. This will sound silly but I could barely reach all 3 keys simultaneously while typing REISUB.

I should add, I was running Ubuntu when I made this misstep; it wasn't from a CD or USB as I later realized I should've been using, while trying to uninstall Win10. Yes I feel like an idiot.

It is in UEFI  mode. Secure boot disabled. Legacy off.
That this fix failed to work, does that give a clue as to what I may've damaged?

I'm embarrassed to lug this machine to the Linux peeps here (it's a monthly meetup) and display my idiocy for all to see, in person.
I really hope I can fix this myself and avoid the shame :(

---

### Post by yancek on 2016-12-28
The best next step if you are still unable to boot the installed Ubuntu is to use or get an Ubuntu install DVD/flash drive and boot it and get the boot repair software from the link posted above by oldfred.  Run it and select the "Create BootInfo Summary" option and post a link to it here.  That should give enough information for someone to make a suggestion to hopefully resolve your problem.   

I'm not sure why you tried to "uninstall" windows.  The standard procedure would have been to simply boot Ubuntu and format the windows partition(s) to a Linux filesystem.

---

### Post by blueviolet2 on 2016-12-28
I thought the tool "OS UNINSTALLER" would be easy for someone like me, who doesn't know how to reformat partitions.
I'd read about doing it that way, and this nifty little tool was mentioned as easier, so I thought I'd be able to do it...here is where it got me :(

---

### Post by oldfred on 2016-12-28
The OS-Uninstaller does not reconfigure partitions. It just makes sure you have correct operating system as the default Boot. Not sure it works with UEFI. 

But expect if you left Windows fast start up on, or its hibernation then it would have problems. Linux NTFS driver cannot correctly see Windows when hibernated. 

If reconfiguring partitions you still have to use a partition tool like gparted.

---

