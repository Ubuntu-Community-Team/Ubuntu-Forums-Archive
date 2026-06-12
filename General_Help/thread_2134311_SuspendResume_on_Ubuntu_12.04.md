---
title: "Suspend/Resume on Ubuntu 12.04"
date: 2013-04-10
forum: General Help
---

### Post by airsoftsoldrecn9 on 2013-04-10
I am having a problem resuming from a suspend state (S3) on my system.

I have attempted following the procedures here:
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

and here:
[https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting)

1. "[COLOR=#333333]suspend_test" did not resume after the designated time period and I restarted the machine with the intent that I could file an automated report with apport. I was never prompted about a report on rebooting into the desktop.
[/COLOR]
2. var/log/dmesg or var/log/dmesg.0 do not seem to contain information about the device preventing resume (maybe I am not using this correctly or I am looking for the wrong things)

Does anyone have a straightforward procedure to find the problem child hardware not wanting to play nicely?

INCLUDED SOME STUFF TO READ BELOW BUT I CAN GATHER MORE:
[ATTACH]241188[/ATTACH]
[ATTACH]241189[/ATTACH]
[ATTACH]241190[/ATTACH]

---

