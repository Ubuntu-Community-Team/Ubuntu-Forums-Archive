---
title: "Chkdsk in Xubuntu?"
date: 2016-12-28
forum: General Help
---

### Post by Malacath on 2016-12-28
Just curious. In Windows there is chkdsk which scans the disk for file system errors and fixes them.

I can't find anything like that on Linux and i've searched the Ubuntu store.

Is the Linux file system immune to errors making check disk not necessary?

---

### Post by Keith_Helms on 2016-12-28
The Linux equivalent is fsck.

---

### Post by Malacath on 2016-12-28
Thanks.

Does that need to be done after booting a live USB?

just typed that in the terminal and got warned that the disk is mounted and will cause errors

---

### Post by Keith_Helms on 2016-12-28
If you want to run it manually, you'll need to do so while the partition is not mounted, so running it from a live USB is one option, yes.  The system will sometimes run it automatically during the boot process based on either the number of boots since the last scan or whether the last shutdown was successful or not (at least that's how I THINK it works).

---

### Post by Malacath on 2016-12-28
Thanks.

 If the system sometimes runs it automatically during boot then I probably don't need to worry about doing it myself

---

### Post by Keith_Helms on 2016-12-28
Unless you have a reason to suspect a problem, I can't see any need to run it manually.

---

### Post by SeijiSensei on 2016-12-28
Ubuntu will fix minor problems during boot, but more serious inconsistencies in the filesystem require manual interventions.

If you're careful about shutting down the system from the menu, or via the "shutdown" or "reboot" commands in the terminal, then you won't have problems.  But if you simply turn off the power, the filesystems will not be unmounted and can be left in an "unclean" state that will need repair the next time you boot.

---

