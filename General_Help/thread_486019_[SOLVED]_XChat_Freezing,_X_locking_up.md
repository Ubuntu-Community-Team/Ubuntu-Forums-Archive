---
title: "[SOLVED] XChat Freezing, X locking up"
date: 2007-06-27
forum: General Help
---

### Post by unnes on 2007-06-27
I recently set up Kubuntu Feisty to dual boot on my previously Vista-only laptop, and the installation process was a cinch and everything seemed to work fine. However, I've found that when I have XChat 2.80 open and unattended for a long period of time (~25-30 minutes), the application freezes and eventually locks up my entire X session.

This doesn't happen when I'm actively using XChat or other programs, but if I leave the computer for a period of time and return, the XChat window is white. I can switch to other open windows and interact with them appropriately, but if I try to close XChat or access the KDE menu, X locks up entirely and I have to reboot.

Since I have a Mobility Radeon 9700, I switched from the default ati driver to fglrx, but that didn't help at all.

I've searched the forums but couldn't find any leads. Any suggestions?

---

### Post by unnes on 2007-06-28
I solved this issue by adding "noapic nolapic" to my kernel-specific GRUB entry.

More information can be found in this thread: [http://ubuntuforums.org/showthread.php?t=412125](http://ubuntuforums.org/showthread.php?t=412125)

---

