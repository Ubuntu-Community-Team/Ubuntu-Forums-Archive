---
title: "Is there a top for IOWait?"
date: 2007-06-19
forum: General Help
---

### Post by mrashley on 2007-06-19
Usually after I suspend and resume and then connect to the internet (but sometimes in neither of those instances) my computer loses responsiveness and my harddrive light stays lit. My "System Monitor" IOWait is fully lit up in this case.

I run 'top' to see if there is any process that's taking up all my computers resources, but it as far as I can tell isn't showing me the runaway process.

Is there something like top but instead shows me what processes are making my computer having IOWait status.

I hope this makes sense.

Thanks!

---

### Post by mrashley on 2007-06-20
For anyone else having this problem. I haven't had any hints as to see how to check what's using up my IOWait time - but I did fix the problem. I had managed to turn off my swap partition (oops!) using the "swapoff" command. 

I re-enabled by issuing

```
sudo swapon /dev/hda5
``` where /dev/hda5 is my swap partition.

If you don't know your swap partition you can find it by typing ```
sudo fdisk -l
``` and look for the one labelled  "Linux swap / Solaris" (supposing, I guess, that you don't have a Solaris file system.

I'd be chuffed if anyone could still advise as to the first problem though. How to find out what program is using up all your IOWait time?

---

### Post by amborle on 2008-04-29
*BUMP*

I have this problem to (mysterious IOWait causing my system to be all sluggish). I have search google until my fingers bled but for no good. hdparm -tT reports excellent values for my disk.

So my simple question is this:

Is there any way to determine what process is causing the IOWait? Running top reveals nothing.

Help please, help.

---

### Post by dcstar on 2008-04-30
> **amborle said:**
> *BUMP*

I have this problem to (mysterious IOWait causing my system to be all sluggish). I have search google until my fingers bled but for no good. hdparm -tT reports excellent values for my disk.

So my simple question is this:

Is there any way to determine what process is causing the IOWait? Running top reveals nothing.

Help please, help.

You may want to install the **atsar** or **systate** packages.

---

### Post by olejorgen on 2008-04-30
I would maybe think that the sinner has a high nFLT (page fault) count. Try enable this column in top.

---

