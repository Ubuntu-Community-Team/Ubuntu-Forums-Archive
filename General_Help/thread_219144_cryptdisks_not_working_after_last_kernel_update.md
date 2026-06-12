---
title: "cryptdisks not working after last kernel update"
date: 2006-07-19
forum: General Help
---

### Post by linuxone on 2006-07-19
Hi,

since the last 2 kernel updates cryptdisks can't be used. Console message is:

> [color=green]/etc/init.d/cryptdisks start
/proc/misc: No entry for device-mapper found
Is device-mapper driver missing from kernel?
Failure to communicate with kernel device-mapper driver.
/proc/misc: No entry for device-mapper found
Is device-mapper driver missing from kernel?
[b]Failure to communicate with kernel device-mapper driver.
Incompatible libdevmapper 1.01.03 (2005-06-13)(compat) and kernel driver[/b]
Command failed[/color]

Until next to last kernel update cryptdisks could be used correctly. All available updates are installed. System is Kubuntu 5.10.

How can I fix this problem? Does this problem really depend on the kernel security update?

Thomas

---

### Post by GTvulse on 2006-07-19
You should file a bug report. The error indicate that the user-space tools are using an older interface library incompatible with the newer kernels.

---

