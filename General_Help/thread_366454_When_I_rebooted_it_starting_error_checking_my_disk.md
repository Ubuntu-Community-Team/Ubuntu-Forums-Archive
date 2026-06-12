---
title: "When I rebooted it starting error checking my disk"
date: 2007-02-20
forum: General Help
---

### Post by billdotson on 2007-02-20
When I rebooting it said that it had been mounted 30 times is is auto-checking the disk for errors and then it said fail and it will try to fix them or something.

---

### Post by moshuptrail on 2007-02-20
It's running fsck.  It will do that every 20-30 times you boot.  That's normal.

What's not normal is the error.  Did it finally boot?  (i.e. was fsck able to repair the file system?)

---

### Post by dcstar on 2007-02-20
> **billdotson said:**
> When I rebooting it said that it had been mounted 30 times is is auto-checking the disk for errors and then it said fail and it will try to fix them or something.

When it boots up, in a terminal do:
```
gksudo gedit /etc/default/rcS
```
and change the relevant line to read:

FSCKFIX=Yes

Then fsck will automatically fix any errors it finds when you next get the 30-mount auto-check.

You can change the default 30 count using **tune2fs**.

---

### Post by billdotson on 2007-02-20
yes it booted and working fine apart from the capture muting automatically when trying to use the microphone

---

