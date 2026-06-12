---
title: "Error message every time I open up a &quot;removable drive&quot;"
date: 2015-01-19
forum: General Help
---

### Post by elvis6 on 2015-01-19
I get this error message literally every time I click to open up a flash drive contents.
It doesn't matter which physical flash drive it is, and it also doesn't make a difference which USB port it's plugged into.
I am able to close out of the error message and then reach the contents of the drive, but the fact that this happens
every single time, is cumbersome and annoying, and I'd really like to know why it happens and how to rid myself of it.

This is the message :

"Failed to mount drive :
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending."

---

### Post by oldos2er on 2015-01-19
If these are NTFS removable drives, they may not have been cleanly unmounted, and would require running chkdsk /f from Windows.

---

### Post by Holger_Gehrke on 2015-01-19
Two guesses:
1) your machine is on the slow side, it was busy mounting the drive automatically and not yet finished with that at the time you clicked and told it to mount it
2) You're double-clicking and thereby telling it twice in short succession to mount it.

---

### Post by elvis6 on 2015-01-19
> **Holger_Gehrke said:**
> Two guesses:
1) your machine is on the slow side, it was busy mounting the drive automatically and not yet finished with that at the time you clicked and told it to mount it
2) You're double-clicking and thereby telling it twice in short succession to mount it.

#2, Single-Clicking does the job.
Thanks !

---

