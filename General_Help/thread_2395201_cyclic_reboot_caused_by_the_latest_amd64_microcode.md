---
title: "cyclic reboot caused by the latest amd64 microcode updater"
date: 2018-06-28
forum: General Help
---

### Post by lvm on 2018-06-28
It happened like this:

using kernel 3.13.0-144 (14.04) - ok
jun 9: installed kernel 3.13.0-149 and rebooted - ok
jun 21: installed some updates including update to the cpu microcode which was set up to execute at the next boot
jun 28: rebooted to the same kernel 149 and the system went into cyclic reboot: shows grub screen, when the default kernel is selected reboots immediately with no messages and without creating any logs, nothing in /var/log with appropriate times
booted to 144 - no issues
tried upgrading to a new kernel (151) - same cyclic reboot
booted back to 144

I am not telling the microcode update is the culprit, but it is mighty suspicious. It cannot be uninstalled using standard tools without uninstalling the kernels packages (linux-generic, linux-image-generic, linux-generic-pae, linux-image-generic-pae). I have both intel-microcode and amd64-microcode installed (CPU is AMD phenom X4 975). Anyone having the same issue? Any ideas?

---

### Post by lvm on 2018-06-28
It is indeed caused by the amd64-microcode package, I rolled it back to the previous version and can boot to latest kernels.

---

