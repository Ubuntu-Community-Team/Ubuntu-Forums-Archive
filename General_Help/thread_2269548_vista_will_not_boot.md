---
title: "vista will not boot"
date: 2015-03-16
forum: General Help
---

### Post by todd13 on 2015-03-16
I installed Lubuntu 14.10 in dual boot mode and now vista won't boot.  It keeps looping through the booting menu.

---

### Post by oldfred on 2015-03-16
Best to see details. Either from your install or live installer add Boot-Repair and post link to summary report it gives.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by todd13 on 2015-03-17
I ran boot-repair and rebooted but vista still won't boot.  Message from boot-repair is listed below.  Also, A symptom I forgot to mention is that the Window's "icon" screen appears momentarily but then goes back to the boot menu.

Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/10613799/](http://paste.ubuntu.com/10613799/)


In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.


The boot files of [The OS now in use - Ubuntu 14.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

---

### Post by carl4926 on 2015-03-17
There are 2 Vista options in the Grub menu
Did you try them both?

---

### Post by Mark Phelps on 2015-03-17
> I installed Lubuntu 14.10 in dual boot modeOK, but HOW did you shink down the existing Windows filesystem partitions to make room for Lubuntu? Did you manually do this using GParted while booted from the Lubuntu install media? Or, did you use the slider in the Installer to shrink the partition? Or did you use the Dism Management utility in Vista to do this?

If you did either of the first two, you likely corrupted the Windows filesystem in the process, and that can render it unbootable.

---

### Post by oldfred on 2015-03-17
You at the very least then need to run chkdsk and perhaps make other repairs to Windows. That cannot be done from Linux.
You really need your Windows repair CD or flash drive or the installer you used to install Vista in the repair console for Windows.

---

