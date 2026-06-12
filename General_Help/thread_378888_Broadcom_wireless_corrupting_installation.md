---
title: "Broadcom wireless corrupting installation"
date: 2007-03-07
forum: General Help
---

### Post by cpetzol2 on 2007-03-07
FYI, I am using Kubuntu

I dont know if this is just a weird coincidence, but I have recently been attempting to install some broadcom wireless drivers via the fw_cutter tool. When you are done installing them, it asks you to reboot, so I do that, and my computer wont start back up. 

If I start Kubuntu normally, the progress bar makes it about 15% and freezes there forever. When I boot Kubuntu in recovery mode, it goes for a while, but eventually freezes up completely, just the same as normal boot mode. There are several lines that have information about my new broadcom drivers, and then there are two lines with some memory addresses and the phrase {child_rip+0}, and that is as far as the boot process will take me.

The first time that this happened, I though it was just bad luck, so I reinstalled Kubuntu. It took me several days to attempt installing the Broadcom drivers again, and I had many successful shutdowns and reboots before then. But yesterday I attempted to install the broadcom drivers again, and as soon as I rebooted, the computer froze.

What am I doing wrong? Is there a way to fix this without having to reinstall everything ? What do I need to do different to prevent this.

Thanks in advance.

---

### Post by cpetzol2 on 2007-03-07
Ok, quick update.

I started Kubuntu in recovery mode and let it sit for a while.

Here is what the last few lines say...

[268.516173] Warning: many lost ticks
[268.516174] Your time source seems to be instable or some driver is hogging interupts
[268.516272] rip ioread32+0x28/0x30


It spit those lines out after about 15 minutes of sitting and doing nothing. I will let it run a while longer and post anything new.

---

### Post by CocoAUS on 2007-03-07
You could probably just add bcm43xx to your /etc/modprobe.d/blacklist file.  That should allow your system to boot.

I would recommend forgetting the bcm43xx driver and instead using ndiswrapper.  It's a much easier process, and the functionality is more complete (get full speed, for instance).

---

