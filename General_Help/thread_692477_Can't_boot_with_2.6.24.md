---
title: "Can't boot with 2.6.24"
date: 2008-02-09
forum: General Help
---

### Post by CTho9305 on 2008-02-09
I can't boot with my 2.6.24 kernel in Gutsy.  I'm not sure I ever booted with 2.6.24 (it's been a while since I rebooted the machine).  When I try to boot, I get:

Decompressing Linux...done.
Booting the kernel.


[18.600189] pnpacpi: exceeded the max number of mem resources: 12
[21.643115] no UART detected at 0x1
[24.359773] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

(and at the bottom of the screen are the two messages, "Kernel alive" and "kernel direct mapping tables up to 100000000 @ 8000-d000")

I can boot fine with 2.6.22-14.

---

### Post by nemarasu on 2008-02-09
try passing:

acpi = no

to the kernel via grub boot menu

---

### Post by mrsteveman1 on 2008-02-09
If you can, get the entire kernel log from one of the failed boots and attach it to a post. You should be able to get the kernel messages from a failed boot from /var/log, it should be called boot.msg or something similar. Might also help to delete the file before trying the boot again so that you dont have to sift through the old logs as well. If root isn't mounting though, there will be no logs for a failed boot.

---

