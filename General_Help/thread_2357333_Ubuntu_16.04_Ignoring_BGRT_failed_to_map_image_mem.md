---
title: "Ubuntu 16.04 Ignoring BGRT: failed to map image memory (emergency mode)"
date: 2017-04-01
forum: General Help
---

### Post by entelechy on 2017-04-01
Hi all,

I have 16.04 LTS which has been running fine until now.  2 days ago there wasn't this issue, but when trying to boot the ubuntu logo loading screen runs for much longer than usual and then I get this:

[        0.031756]  Ignoring BGRT: failed to map image memory
/dev/sda2: recovering journal
/dev/sda2: clean, 473140/120496128 files, 410775332/481978369 blocks
system logs, "systemct1 reboot" to reboot, "systemct1 default" or ^D to 
try again to boot into default mode.
Press Enter for maintenance
(or press Control-D to continue):


I've been trying to figure out what this is, but have only found issues discussed online that are similar to this

Thanks

---

### Post by entelechy on 2017-04-01
Deleted a line I'd added to fstab and now the issue is corrected.  What is the reason that this line caused the issue:

/dev/sdd1      /media/samsung32       ntfs-3g        defaults,locale=en_US.utf8    0    0

Is it because of not using the UUID number here instead?  All other drives are using the UUID in fstab currently

---

