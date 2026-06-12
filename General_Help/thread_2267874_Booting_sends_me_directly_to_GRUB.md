---
title: "Booting sends me directly to GRUB"
date: 2015-03-04
forum: General Help
---

### Post by tom167 on 2015-03-04
I recently Installed Xubuntu to try it out, and I wasn't going to use it.
I already had my Windows 8.1 Pro and Ubuntu 14.04.2 installed, and I installed Xub over them.
I erased the partition (which now wasn't a good idea) and then went on with my daily doings.
What ended up happening was when I was restarting my computer, I was directly sent to the GRUB.
The only way I was able to fix this was to set a root and restart the grub menu.
This did not fix the restarting problem.
If I get into the Kernel, I see weird symbols everywhere, but I am able to boot into ubuntu.
Any help?

---

### Post by oldfred on 2015-03-04
If you have BIOS with MBR, the last install controls MBR and the small part of grub in MBR has to load the rest of grub from your now missing partition.
Or if UEFI, the grub.cfg in the efi partition points to the missing partition. That could be quickly edited to have correct partition if old install is ok.
Which do you have UEFI or BIOS?
All Windows pre-installed have UEFI.

Best to see details. 
Post link to summary report:
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by tom167 on 2015-03-04
I just reinstalled Ubuntu and got it working. Thanks.
btw, mine was UEFI.

---

### Post by oldfred on 2015-03-04
Sometimes that is the easiest.

But you probably just had to reinstall grub.

---

