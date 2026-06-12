---
title: "External USB boot can't find partition by UUID"
date: 2007-08-02
forum: General Help
---

### Post by Steven_B on 2007-08-02
I have Ubuntu installed on an external USB drive.  I originally installed Dapper, and it worked great.  However, after upgrading it to Edgy, it won't boot.  GRUB comes up, and I can select which kernel to boot.  It hangs shortly after that, and brings me to a command prompt.
The problem is that it cannot find the USB drive's partitions by UUID.  "ls -l  /dev/disk/by-uuid" shows only partitions from the internal drive.
When I hard-code the root partition in the menu.lst file, it boots properly.  Once booted, "ls -l /dev/disk/by-uuid" shows all of the partitions on the external drive.
I really need UUID's working, as I hope to boot the drive from multiple computers.
Any ideas?

---

