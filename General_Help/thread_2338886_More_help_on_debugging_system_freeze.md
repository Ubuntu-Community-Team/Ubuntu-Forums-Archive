---
title: "More help on debugging system freeze"
date: 2016-10-02
forum: General Help
---

### Post by doctorbrown on 2016-10-02
I have been running Ubuntu 14.04 for several months now. It's been stable up until recently. But lately it has been freezing for no apparent reason. I can't switch to the console. The mouse and keyboard stop responding, not even to C-A-D. I can't remote connect into the system. I have searched the forum and found the following post that is similar:

[https://ubuntuforums.org/showthread.php?t=1318262&highlight=debugging+system+freeze](https://ubuntuforums.org/showthread.php?t=1318262&highlight=debugging+system+freeze)

I have looked at the log files as suggested but don't see anything that I recognize as pointing to the problem. The only errors I find are:
```
kern.log:Oct  2 11:07:07 Johne-xxxxx kernel: [    0.014923] ACPI Error: [\_SB_.PCI0.XHC_.RHUB.HS11] Namespace lookup failure, AE_NOT_FOUND (20150930/dswload-210)
kern.log:Oct  2 11:07:07 Johnedxxxxx kernel: [    0.019561] ACPI Error: 1 table load failures, 7 successful (20150930/tbxfload-214)
kern.log:Oct  2 11:07:07 Johned-xxxxx kernel: [    0.202796] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
kern.log:Oct  2 11:07:07 Johned-xxxxx kernel: [    1.412970] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro

```
Are these pointing to something that is could be related to the freeze?

I have tried to run monitoring tools, like top to see if I can capture something about what processes might be involved, but so far no data is captured that points to anything.

The most significant changes I have recently made to the system is to install the Bacula and BackupPC packages, and associated dependencies. I am in the process of evaluating which one I want (or neither) to use to backup my system.

If this were Windows, I'd start disabling running apps and services to try and locate which is causing the problem, but I'm not sure how to determine which apps can be disabled (and how to do it) and still have a running system. I know where some of the startups occur, but any additional pointers would be helpful.

Are there any other techniques I can use to debug this system freeze? Thank you in advance for any help you can provide.

---

