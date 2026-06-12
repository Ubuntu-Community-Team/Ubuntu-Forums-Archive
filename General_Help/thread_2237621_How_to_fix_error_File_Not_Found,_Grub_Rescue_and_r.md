---
title: "How to fix error File Not Found, Grub Rescue and restore MBR."
date: 2014-08-03
forum: General Help
---

### Post by knight2 on 2014-08-03
**Problem:**
How to fix **Error: File Not Found, Grub Rescue >**
How to **restore MBR **on a windows when Grub is corrupt.

**You will need:**
You will need a working computer (Ubuntu/Linux) with Unetbootin (or Live USB Creator of your choice) installed on it. You will also need gparted-live.iso (whatever is the latest release).

**Solution:**
Download gparted-live-xxx.xxx.iso
Use Unetbootin to make a liveUSB of gparted-live ISO.
Plug your USB in to the impaired computer and boot. Set your bios to boot from USB if necessary.
Select language of your choice.
Select GUI when asked.

Once you are in the graphical user interface:
Right Click, and find **TESTDISK** in the menu and click on it.
Select Drive of your choice and PROCEED
Select Partition: **[Intel]**
Select **[MBR Code]** to write MBR CODE. This option will REMOVE GRUB completely and install MBR on the boot sector.
Restart.

**Enjoy.**

---

### Post by Bucky Ball on 2014-08-03
Now that you've removed Grub completely, how are you going to boot Ubuntu??? You give no instructions for reinstalling it ...

You also don't mention anything about UEFI or legacy install/boot.

Are you talking about after you remove Ubuntu and are wanting to revert back to Windows machine only, follow your instructions? :-k

---

