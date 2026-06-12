---
title: "Windows hard drive died, now I can't boot into Ubuntu."
date: 2007-03-17
forum: General Help
---

### Post by super breadfish on 2007-03-17
I have two hard drives in my computer. One, an IDE drive, has Ubuntu 6.10 installed, and the other, a SATA drive, is partitioned in two, with one partition for Winows XP and the other for back ups. 
The SATA drive has been having problems for a while, and it now appears to have died. The IDE drive with Ubuntu is still ok, however my computer no longer boots. Grub either gives an error message or does not appear at all. I don't think the computer can access the boot sector on the SATA.
How can I boot from the IDE drive? I'm not exactly an expert with problems like this and don't know what to do. Can Grub be reinstalled or moved to the IDE drive? Or am I stuck?

---

### Post by peabody on 2007-03-17
Yes, Grub can be reinstalled.  You'll want it installed to the MBR of the IDE drive.  There would be a few ways to go about this.  Methinks what may be more likely a candidate is to simple boot from the LiveCD and follow these directions:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by hal8000 on 2007-03-17
The first thing to do is recover some of your data, and for this you need a live CD.
I'm not sure about the live Ubuntu CD, someone else in the forum will help you,but if you have a live knoppix cd, put that in the cdrom and boot.

When the desktop appears, you will see your drives as icons, just plug in a USB stick  (which will open in a window) and transfer the files you wish to save, knoppix uses kde as standard so you should be ok.

The live version of Ubunti 6.04 may also work (distro does not have to match in a lie enironment).
You may not be able to recover all data from the windows driive depending on the type of fault, but some may be recoverable.

To reinstall grub, you may first want to swap the drives and make the ubuntu drive master. To reinstall grub have a look at this link:

[http://josephhall.org/grub_install_hda1.html#reinstall](http://josephhall.org/grub_install_hda1.html#reinstall)

---

