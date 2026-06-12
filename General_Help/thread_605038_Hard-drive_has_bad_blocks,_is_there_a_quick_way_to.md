---
title: "Hard-drive has bad blocks, is there a quick way to identify and blacklist them?"
date: 2007-11-06
forum: General Help
---

### Post by Fox5 on 2007-11-06
Hey all,

I'm currently trying to do a fresh install of ubuntu on a laptop with a hard disk with bad blocks.
I've already installed ubuntu, and then went into the recovery console and ran fsck -c -y (after umounting the drive)...and it's been running for days and it's only about halfway done!

Is there any quicker way to identify and quarantine bad blocks (this is a temporary solution of only of course, I'll work on replacing the drive eventually)? I'm not concerned about losing any current data, just want the laptop working reliably and this bad block checking finished as soon as possible.

I'm assuming that fsck -c on an installed OS does a non-destructive write test for bad blocks. I've heard that there's also a destructive write test that's faster. If I interrupt this fsck, would it be possible to do a faster test off a livecd and then install ubuntu? It's really ridiculous that this fsck -c will likely take over half a week to complete.

---

### Post by dcstar on 2007-11-06
> **Fox5 said:**
> Hey all,

I'm currently trying to do a fresh install of ubuntu on a laptop with a hard disk with bad blocks.
I've already installed ubuntu, and then went into the recovery console and ran fsck -c -y (after umounting the drive)...and it's been running for days and it's only about halfway done!

Is there any quicker way to identify and quarantine bad blocks (this is a temporary solution of only of course, I'll work on replacing the drive eventually)? I'm not concerned about losing any current data, just want the laptop working reliably and this bad block checking finished as soon as possible.

I'm assuming that fsck -c on an installed OS does a non-destructive write test for bad blocks. I've heard that there's also a destructive write test that's faster. If I interrupt this fsck, would it be possible to do a faster test off a livecd and then install ubuntu? It's really ridiculous that this fsck -c will likely take over half a week to complete.

Possibly the **smartmontools** package can be used to kick off a thorough SMART test of the disk, and that may be able to mark/remap the blocks.

---

