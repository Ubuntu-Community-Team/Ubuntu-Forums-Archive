---
title: "Installing WinXP under Qemu"
date: 2007-03-30
forum: General Help
---

### Post by GrumpyBob on 2007-03-30
I'm running the Feisty beta on an IBM Thinkpad R52.  I'm actually very happy with Feisty, no major problems other than cosmetic issues with Beryl.

I have installed Qemu for running Win98 for a few Windows apps.  the laptop has an NTFS partition with WinXP, and a FAT32 partition for restoring WinXP - I've never used that, as I very rarely boot into or use WinXP on this laptop.

My question is whether it would be possible to install WinXP in Qemu from the restore partition...

Robert

---

### Post by srhlefty on 2007-04-10
Hi Robert,
I'm no expert at this sort of thing, but my guess is no.  However, I believe that VMware Workstation can take an existing partition and turn it into a VM, which you would then be able to run from ubuntu.  This is not an option I have explored personally, though I have used VMware to install XP fresh and then proceed to install windows apps.  I know also that you can share partitions of your physical hard disk with VMware so that the VM has access to your data.  Is that the sort of thing you would need?

---

