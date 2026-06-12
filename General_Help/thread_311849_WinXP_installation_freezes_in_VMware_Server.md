---
title: "WinXP installation freezes in VMware Server"
date: 2006-12-03
forum: General Help
---

### Post by celsofaf on 2006-12-03
I don't know whether this is the right place to post it on the forum. The forum search function didn't help me either with my problem.


I followed the guide at [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209) to install VMware server on my machine. Allocated 15GB to my virtual machine, loaded the Windows XP disc, "booted" via VMware and started the installation procedure. It froze when "detecting and installing devices".

I looked at the VMware configs and found no clue about it. Any thoughts?

Thank you!

---

### Post by LLRNR on 2006-12-03
For me it worked, I followed the exact guide you pointed to... :-k Sounds stupid, I know, but I didn't have any "device" attached to my computer when installing XP in VMware Server... you know, only the usual: the monitor, the keyboard and the mouse.

Also, it depends on the amount of RAM you assign to your virtual machine, it's "taken away" from your actual RAM - for instance, I allowed the virtual machine to have 160 MB RAM out of my actual 384 MB, and, since things were going *really slow*, I didn't do anything else when I was installing the guest OS, I let VMware work quietly and I didn't disturb the install process by any means...

LLRNR

---

### Post by celsofaf on 2006-12-03
Heh... I did nothing special (nothing was connected, by the way), turned the virtual machine off, then on... and now it works. :)

Go figure... But thanks!

---

