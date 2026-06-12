---
title: "Memtest86+ HowTo for 12.04.2?"
date: 2013-06-23
forum: General Help
---

### Post by alvinmoneypit on 2013-06-23
I am looking to use this program, but no idea where to find it or how to configure it to show me results.  
I wish to test some memory on a system I'm building.
Yes, it is installed according to software center.

---

### Post by ajgreeny on 2013-06-23
You only see memtest when you are booting and see the grub menu, so if you have a single OS system you may never see it listed as grub menu will not show by default; you do not run memtest from another running OS, ie not from your Ubuntu system, only when booting it.  If you want to see the grub menu to run memtest hold shift down straight after the POST has finished.

You can also run it from a live CD when booting that; it will appear in the menu that you see from a live system boot, but again, not from the running live OS, only at boot time.

---

### Post by cool110 on 2013-06-23
As Memtest86+ require full direct access to the memory it can only be run at system boot before the Linux kernel is loaded. Hold shift when booting the computer to force the GRUB menu to appear and then select Memtest86+ instead of Ubuntu.

---

### Post by alvinmoneypit on 2013-06-23
Thanks, folks!

---

