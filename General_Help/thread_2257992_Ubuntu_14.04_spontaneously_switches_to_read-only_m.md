---
title: "Ubuntu 14.04 spontaneously switches to read-only mid session"
date: 2014-12-24
forum: General Help
---

### Post by cluelesswonder on 2014-12-24
My system has been acting strangely for the past couple of sessions. . .it seems to be getting worse each day.
The most harrowing issue is when I get this:
/usr/lib/update-notifier/update-motd-update-available 39: cannot create /var/lib/update-notifier/updates-available: Read-only file system 
when trying to update (or do anything with sudo) in the shell because in the middle of a GUI session, sudo claims that my usr's home directory does not exist/is not mounted and my whole system has turned to read-only (>.<)

I'm not sure if it is related, but prior to this happening firefox/thunderbird crash constantly.

Any idea what the problem is/how to solve?

---

### Post by coldraven on 2014-12-24
Check your hard drive for errors, run Disk Utility then look at the Smart Data.
I have this problem using 12.04 but have not got around to replacing the drive.
I do not get a warning that the drive has gone read-only. An easy way to check is take a screenshot and if it is unable to save then it's time to reboot :(

---

### Post by cluelesswonder on 2014-12-24
There are no apparent errors on the hard disk and SMART test completes with Disk status 'OK'. There is a g-sense error rate of 40 but I got the disk new in April and tested it and the computer/hard drive has just been sitting on my desk since then.
I CAN reboot when the system suddenly changes to read-only and this does fix the problem. . .at least temporarily, but I'm afraid that there is a much bigger problem that would be better to address than just keep rebooting and hope it goes away on it's own. I just don't know what that problem is. . .

---

