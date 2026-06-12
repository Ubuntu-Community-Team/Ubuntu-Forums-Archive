---
title: "Failed to start up manager, freezing"
date: 2019-02-01
forum: General Help
---

### Post by bbentelin on 2019-02-01
When I tried to reboot my system today, the boot screen lists:

/dev/sda1: clean 313602/7315456 files, 23628736/29252349 blocks
[!!!!!!] Failed to start up manager, freezing
[ ] systemd[1]: Freezing Execution.


I tried to boot in recovery mode, but the same thing happens, albeit with a bit more information:

Welcome to Ubuntu 18.04.1 LTS

...

Failed to open serialization file: Read-only file system
(sd-executor) failed with exit status 1
Failed to start up manager, freezing


It passed the memory test without any errors.

Do I need to boot from cd/usb to work through this?
Or is there something I can do from the grub command line?

---

