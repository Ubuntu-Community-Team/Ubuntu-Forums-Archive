---
title: "Ubuntu will not boot (problems with H-T P4?)"
date: 2008-04-27
forum: General Help
---

### Post by bobbymilla on 2008-04-27
hiya all, ive been trying to install Ubuntu for some time now, but each time i install it on my machine and i start it booting, the bar underneath the Ubuntu logo stalls and freezes, forcing me to perform a forced restart. This happens whenever i boot. My system Specs are as follows:

Intel P4 Hyper-Threaded Processor at 3.0 Ghz
1gb of DDR2(2x 512mb)
Asrock Motherboard
PNY geforce 7600 GT

I was wondering if you had experienced this problem before or if you had any boot commands that i might try. :confused: I was wondering if the problem might be caused by Hyper-Threading on my Processor. Thanks,:) !

---

### Post by rubicon on 2008-04-27
> **bobbymilla said:**
> I was wondering if the problem might be caused by Hyper-Threading on my Processor.Not likely. Try this:
press Esc on GRUB boot screen, and remove flags "quiet" and "splash" from your default boot line. Thus all boot messages will be visible. Next time you boot all changes will be lost, so be aware you may need to edit boot file again later (or edit it manually in /boot/grub/menu.lst for permanent effect).

---

