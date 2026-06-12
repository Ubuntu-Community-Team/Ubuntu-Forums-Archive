---
title: "Disable the need for user input at boot time (for disk checks, etc)"
date: 2012-12-03
forum: General Help
---

### Post by c01e on 2012-12-03
Hi,

I've disabled disk checks via:
```
sudo tune2fs -c 0 -i 0 /dev/sda1
```

And set the /etc/fstab dump and pass columns to 0.

However every time the power is cut to the computer, it wants to do a disk check! How can I determine why ubuntu wants to do a disk check?, when tune2fs was told not too. If there is no way to determine this (via a command or log file). Any ideas why is happening (maybe it has an error, which forces the disk check)?

Anyway, assuming I can't stop this disk check. It also asks a user to click a keyboard button to continue, or another keyboard button to cancel. Which is every painful, when no one is around to press the keyboard button (since this computer is not generally around humans, just another computer that can control its power via a relay switch).

Cheers,

---

### Post by dcstar on 2012-12-03
> **c01e said:**
> ]
I've disabled disk checks via:
.....

[LIST=1]
[*]You are a fool disabling things designed to keep your system working and your data intact.
[*]Set this in /etc/default/rcS:
```
# automatically repair filesystems with inconsistencies during boot
FSCKFIX=yes
```
[/LIST]

---

### Post by c01e on 2012-12-03
Yeah, I do know the manual is against this, but this fool has hes reasons (work arounds). Anyway, looking at the man for rcS it says FSCKFIX is set to say yes on all disk check questions. But how do you tell ubuntu to start the disk check? (without the need for a human to click a keyboard button).

Cheers,

---

