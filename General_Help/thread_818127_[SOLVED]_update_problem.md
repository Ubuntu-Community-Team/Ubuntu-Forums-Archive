---
title: "[SOLVED] update problem"
date: 2008-06-04
forum: General Help
---

### Post by astd on 2008-06-04
Today new kernel have been released, I downloaded and installed but after restarting my system i still have an older kernel version 2.6.24.16.
What can i do to update my system for newer kernel version?

---

### Post by Sef on 2008-06-04
Go into GRUB and check that the new kernel is there.  To go into GRUB, press esc upon start.

---

### Post by astd on 2008-06-04
I think is have been installed wrong or with some problem there is a way to uninstall the update and then try to update again?

---

### Post by Ameneon on 2008-06-04
Did you choose to keep the old menu.lst or to replace it? If your new kernel file is in /boot but is not seen in the bootup menu then chances are you just need to edit the menu.lst file (in /boot/grub) in order to load the correct kernel.

On a tangent, from what I understand the wording in the upgrade is a bit unprecise as it states that the menu.lst will be replaced but rather what is correct is that it will be updated (hence any tweaks to the file will be retained), or am I uncorrect here? Could be worthwhile to update as many of us noobs have a tendency to go the "if it ain't broke don't fix it" route.

---

### Post by astd on 2008-06-04
I have fix it by adding new kernel to Vista bootloader with another program "Eastbcd".
All working great.
Thanks for your help.

---

### Post by Sef on 2008-06-04
You're welcome.  Thank you for posting how you resolved your problem, and please keep asking any questions you have.

---

### Post by ppttpp on 2008-06-04
Was the new kernel released in Ubuntu packages?

---

