---
title: "can't repair GRUB2"
date: 2016-01-12
forum: General Help
---

### Post by duffrecords on 2016-01-12
I have 4 LVM volumes (boot, root, srv, and swap) on top of software RAID 10.  Each disk is 3 TB so there is a 1 MB BIOS boot partition on each one.  Yes, I know, this is not the wisest setup.  If I could have gone back in time and designed it differently, I would have put boot and root on a single disk, separate from the RAID, but I only had 6 SATA ports and wanted to maximize the amount of storage space available.  I was able to install the system but, ever since, it has been difficult to maintain.  Often when I update GRUB or the kernel I run into boot loader issues, which I can usually fix by reinstalling GRUB.  This time, however, the computer rebooted into the grub rescue prompt and was unable to boot up further.

Troubleshooting steps taken:

Basically, when I set prefix=(lvm/vg_raid10-boot)/grub that folder is empty, so when I try to insmod normal or insmod linux, it can't find those modules.  There is a grub.bak folder on that volume, so I tried that.  I was able to insmod normal and reach the regular grub prompt but when I tried to insmod linux, it says "invalid arch-dependent ELF magic."

I booted from an Ubuntu live CD, installed boot-repair, and proceeded with the recommended repair.  After rebooting, it went back to the grub rescue prompt again.  I booted into the live CD and tried it again but this time the boot-repair process seems to get stuck while replacing the kernel.  The progress bar has been in the same state for hours and the log is filling up with "SET@_progressbar1.pulse()" messages.

What should I do to repair GRUB?  Here is a paste from the first time I ran boot-repair:
[http://paste.ubuntu.com/14475880/]("http://paste.ubuntu.com/14475880/")

---

### Post by oldfred on 2016-01-12
I do not know RAID nor LVM.
But thought with either that you do not install grub to the MBR of a hard drive but to the root of the RAID or LVM volume. But that may depend on the type of RAID.

So I would think grub gets installed to /mapper/....??
/dev/mapper/vg_raid10

---

