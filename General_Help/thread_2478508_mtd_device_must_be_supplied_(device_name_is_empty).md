---
title: "mtd device must be supplied (device name is empty)"
date: 2022-08-28
forum: General Help
---

### Post by JimLS on 2022-08-28
Have 22.04 on a dell 7040.  Was running ok (AFAIK).  I have a small SSD and was modifying fstab to mount the HDD (second drive).  Had a power failure but wasn't saving a file at the time and was done with edits.  Now it won't start and comes up with the title line and:
Your are in emergency mode.  After logging in, type "journalctl -xb" to view
system logs, "systemctl reboot" to reboot, "systemctl default" or "exit" 
to boot into default mode.
Press Enter for maintenance
(or press Control-D to continue):

I see a number of other posts on this but most say it doesn't stop booting which it does stop mine.

Not that experienced with this depth of the OS and not sure if my edits caused this.

---

### Post by JimLS on 2022-08-28
I had made an error in the UUID of the new HDD.  Fixed that and the system boots.  Would have removed this thread but didn't see a way to do that.

---

