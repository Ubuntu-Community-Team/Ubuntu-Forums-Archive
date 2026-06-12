---
title: "Is my drive failing?"
date: 2007-10-05
forum: General Help
---

### Post by Adam314 on 2007-10-05
I'm running ubuntu, I think 7.04 Feisty Fawn (I originally installed something earlier, but have since upgraded).

My computer crashed a few days ago.  I usually leave it on all the time.  When I got to it, the monitor was off (power save), which is normal, but it wouldn't come on when when I moved the mouse or pressed on the keyboard.  I pressed the reset, it came back up, and seemed normal.
A few days later (today), when I got to it, it was in a text-mode screen with some errors about /dev/hda2.  I rebooted (pressed reset button), and it said it was running fsck because it had been 30 boots since last run.  There were some errors that came up, it said it exited with status 3, which I'm assuming is the sum of 1 (errors were corrected) and 2 (system should be rebooted).  Before I could read more, the system rebooted on it's own.

So now two questions:
Is there a log that contains the messages that appeared during the previous boot?
What checks/tests should I run to see if the drive is failing?

My drives:
    /dev/hda1   swap
    /dev/hda2   OS
    /dev/hdb1   swap
    /dev/hdb2   data

Thanks!

---

### Post by peabody on 2007-10-05
Check the dmesg and /var/log/messages files for anything related to I/O.  If filesystems are determined to be bad, the filesystem in question will usually be remounted read-only on the fly.

---

