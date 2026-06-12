---
title: "Am I running 2 kernals?"
date: 2013-11-29
forum: General Help
---

### Post by miguel6 on 2013-11-29
I pulled my SSD out of my other laptop and without do any reformatting, I just plugged it into my new laptop. I did this because from past experience of installing Ubuntu I noticed the installation has the option to over write and "erase" the previous copy of Ubuntu. That is what I did. Now, I may have misunderstood this feature and it doesn't actually erase anything but just overwrites there for I suppose I could be running 2 kernals right now? 

The problem I'm having as of a result of this is, whenever I turn my laptop OFF it will shut down and turn back on right away. It's as if it is restarting and not shutting down. So for the past few days my laptop has just always been on and I just put it on suspend when I close to lid.

Any help is appreciated.

Acer Aspire V5 571
Pretty much virgin Ubuntu 13.10, I just installed JDK, MySQL server, Netbeans, IntelliJ, FileZilla, Chrome. So I mean I haven't done any modifications to the system files of some sort.

I get a crash report on start-up. I'm not sure how to post it here. I can't copy paste.

---

### Post by grahammechanical on 2013-11-29
We cannot run two kernels at the same time. An update to Ubuntu may also update the kernel. The old kernel is still on the hard disk and we can choose to boot it by selecting a previous kernel at the Grub menu. You will see them in the Advance Options for Ubuntu sub menu. A new or re-installation will overwrite the partition to avoid having conflicts between old and new configuration files.

My guess it that Ubuntu is configured to run on the hardware of the old laptop and although it is booting on the hardware of the new laptop it is not configured specifically for the new hardware.

You may not have modified the system files and I do smile at your definition of "virgin Ubuntu" what with all that additional software installed. But you most certainly have modified the hardware.

Regards.

---

