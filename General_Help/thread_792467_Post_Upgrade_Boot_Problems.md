---
title: "Post Upgrade Boot Problems"
date: 2008-05-12
forum: General Help
---

### Post by rossdub on 2008-05-12
I applied the latest updates to my desktop Hardy system, and now I'm having problems booting.  GRUB loads fine, but the system fails to boot properly.  I believe the problem is on my 400 GB WD SATA hard drive.

If I select regular mode, the system goes into a loop of hanging on the splash screen, then rebooting back to grub.  

If I select recovery mode, the boot sequence gives the following message before the entering into the same hang and reboot loop:

ATA_2 Timeout waiting for ADMA IDLE stat=0x440
ATA_2 Timeout waiting for ADMA LEGACY stat=0x440

I've also tried booting from a Gutsy LiveCD and a Puppy Linux Live CD.  Both hang then reboot when trying to read from the hard drive in question...I'm hoping that this doesn't mean it's a complete hard drive failure, but I'm not so sure.  

Anyone seen this type of thing before?  I have some data on this drive I'd like to access, so if anyone has any suggestions, even if it is just how I can access my /home folder for backup then do a reinstall, please pass them along.  So far, I cant' get anything to boot when this disk is plugged into the motherboard.  Thanks in advance.

---

### Post by little8020 on 2008-05-13
you may have currupted the boot files?
On my comp i used wubi to dual-boot and i think i corrupted my boot files because it wouldn't boot xp or ubuntu but it read the live cd and i did a full install of ubuntu

---

### Post by rossdub on 2008-05-13
Ok, I also turned off quiet mode on the boot to see if I could find some more information...here is the output:

Loading essential drivers...
running /scripts/intit-premount     ok
Mounting root file system...
Running /scripts/local-top          ok
Waiting for root file system...     ok
Running /scripts/local-premount     ok

The progress bar freezes and the system reboots itself there.

---

