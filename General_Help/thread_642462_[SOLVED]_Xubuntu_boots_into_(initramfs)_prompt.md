---
title: "[SOLVED] Xubuntu boots into (initramfs) prompt?"
date: 2007-12-16
forum: General Help
---

### Post by teryowen on 2007-12-16
Alright so I installed Xubuntu 7.10 by connecting the hard drive of an older computer to my newer one installing it on that hard drive and then connected it back to the old computer(sony 128mb ram, pentium 2), now i edited all the grub files accordingly as well as the fstab. I starts up the machine and choose to boot into xubuntu, after a bit of loading it says its dropping to a shell and then all im stuck with is a prompt like terminal but looks like this:

(initramfs)

when i go to the root dir and do ls there is no boot folder :S

So how do i stop this initramfs prompt from happening and boot into some sort of desktop environment or atleast something similar to terminal because in this prompt some commands don't work like fdisk?

Any ideas on what to do?

---

### Post by teryowen on 2007-12-16
SOLVED:

Hey i figured it out i thought i had set up the fstab correctly but i mispelled on eof the drive letters screwing everything up. but now everything runs fine.

---

