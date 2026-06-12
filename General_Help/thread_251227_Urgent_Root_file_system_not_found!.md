---
title: "Urgent: Root file system not found!"
date: 2006-09-05
forum: General Help
---

### Post by mycroft on 2006-09-05
Ubuntu crashed on me an hour ago - complete lockdown with no response to input from mouse or keyboard. I restarted, and the boot process halted with a message stating that several key folders could not be found, and that in fact the entire root file system seemed to be missing. This has happened out of the blue - haven't installed or removed anything for the past week or so.

I booted into Windows and started Explore2fs (a little program for reading ext2/ext3 file systems in Windows) - my file system was there all right, and I was able to read and extract files from it too. In my opinion, this would suggest I'm not dealing with hardware failure.
I noticed that grub, in trying to mount the root file system, was searching for /dev/hda6, even though the partition in question was identified as hda3 by Explore2fs. I tried booting with grub boot parameters set for dev/hda3, but to no avail.
What do I do?

---

### Post by mycroft on 2006-09-05
Strange. Very strange indeed.
I surfed the Internet through Windows for a while, and then decided to reboot into Ubuntu and check which system commands were still available to me. Ubuntu booted flawlessly - much to my amazement, as I hadn't made any permanent changes.
I ought to be glad, but it is actually rather disturbing to me that this problem arose and went away on its own.

---

### Post by bernied on 2006-09-05
A possibility:
If the machine crashed there may have been parts of the filesystem left in a damaged state. On startup, ubuntu would run fsck, which checks for disk errors and fixes them, but maybe this wasn't until the second reboot.

---

### Post by PriceChild on 2006-09-05
> **bernied said:**
> A possibility:
If the machine crashed there may have been parts of the filesystem left in a damaged state. On startup, ubuntu would run fsck, which checks for disk errors and fixes them, but maybe this wasn't until the second reboot.

Hmm... i think the root file system has to be mounted though to run fsck?

Ah well... i wouldn't worry about it... just make sure you keep backups of ALL important data!

---

