---
title: "Reboot with custom GRUB2 config file one-time only?"
date: 2014-05-04
forum: General Help
---

### Post by marinosr2 on 2014-05-04
I run a dual-boot system, and I've made a script that reboots to Windows using grub-reboot to specify Windows as the default OS for one-time only. When I reboot, though, it still waits at the GRUB boot screen for ten seconds. Is there a way that I can get GRUB to boot with a custom grub config file once (with the timeout set to 0) so that when I run this boot into windows script it bypasses the boot menu? I would prefer to not have to kluge it with copying a custom config file once in the reboot script, and then running a separate script on Ubuntu startup to copy the original config file back.

---

