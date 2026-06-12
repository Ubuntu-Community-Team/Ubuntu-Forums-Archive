---
title: "Suddenly, I Lost half of my hard disk partitons"
date: 2013-10-02
forum: General Help
---

### Post by KxWWFhY on 2013-10-02
Hello, 

I lost half of my hard disk partitions like 275 Gb from my 500 Gb HDD i was running Ubuntu 12.04 x64 + windows 7 pro x64, after losing the partition i lost the access to each of the operating system even that i was still have the windows 7 partition i did a fix to the grub by using boot repair and nothing happened still have this msg "Multiple partitions". 

Now i want to know if it's possible to recover that big lost even some of it and if not so how can i rebuild my partitions again by using ubuntu or linux.

---

### Post by Bucky Ball on 2013-10-03
*Thread moved to **General Help**.*

Welcome. As you are getting a 'multiple partitions' error probably not a problem with the actual hardware. Did you do anything specific, or were doing something specific, then this happened?

Can you boot from an install disk/USB, 'Try Ubuntu', when you're at a desktop launch Gparted and see if the partitions are still there. Also, if you could run Boot-repair and create a boot-info, post it and a link to it here. That will tell all ...

You weren't by any chance attempting to add another partition when this happened? Do you have four partitions on there already?

---

### Post by KxWWFhY on 2013-10-03
i did not do anything wrong i guess i was sleeping and when i get up i found my pc restarted and all of that happened after that unknown restart, 
here's what i did: i absolutely run an ubuntu live cd to see my partitions, i found just two partitions and all the other partitions gone "Empty" from the disk utilization and unmounted, and my hard disk was containing of 4 ntfs partitions, 1 for swab and 1 ext4 for ubuntu 12.04 so the total will be 6, now i installed win 7 so i can't bring to you the boot repair info cuz it already gone. so is it possible to figure out what happened and to recover any of that damage?

---

### Post by Grenage on 2013-10-03
Probably not, now that you've gone and installed an entire OS on the drive.

You could try data recovery tools, but it's going to be pot luck.  It's probably an idea to health-check your hard drive, but to be honest, if there was a hardware glitch, it would be far more likely that your entire partition table would end up wrecked.

---

### Post by KxWWFhY on 2013-10-03
> **Grenage said:**
> Probably not, now that you've gone and installed an entire OS on the drive.

You could try data recovery tools, but it's going to be pot luck.  It's  probably an idea to health-check your hard drive, but to be honest, if  there was a hardware glitch, it would be far more likely that your  entire partition table would end up wrecked.


okie, so what tool to use ? and i know that it's not to completely get my data back. and i want to know how to test my hard disk driver to know it's health and there is no crash on it better to name the tool too. cuz what driving me crazy is the fact that i want to know why that happened

---

