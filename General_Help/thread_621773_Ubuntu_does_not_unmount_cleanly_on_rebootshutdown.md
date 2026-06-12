---
title: "Ubuntu does not unmount cleanly on reboot/shutdown"
date: 2007-11-24
forum: General Help
---

### Post by se2131 on 2007-11-24
About a week and a half ago, ubuntu told me that both of my ext3 partitions were not unmounted cleanly, and it had to run an fsck. This died with exit code 4, and I had to run it manually. It turned out that there were lots of illegal blocks, and basically it deleted a ton of inodes.

I thought the issue was fixed, but it happened to me again just now, and what's more worrisome is that I actually lost some files.

I'm shutting down the computer properly, using either shut down or restart, and it goes to completion, so I'm not sure why it wouldn't be unmounting properly.

---

### Post by se2131 on 2007-11-24
bump

---

### Post by se2131 on 2007-11-26
Ok, I'm losing data with every reboot, if anyone has ANY ideas, please let me know.

Sometimes my files show up in lost+found, but most of the time they don't.

---

### Post by hikaricore on 2007-11-26
I don't mean to be a negative nancy here, but is it possible your hard drive is failing?

If you have another drive sitting around you're not using I suggest swaping it out, trying a fresh install on it, and trying the same things that have been causing your current issue.  If everything works fine then it's likely the previous drive.

I know not everyone has a spare hard drive, but it's worth a shot.

---

### Post by se2131 on 2007-11-26
> **hikaricore said:**
> I don't mean to be a negative nancy here, but is it possible your hard drive is failing?

If you have another drive sitting around you're not using I suggest swaping it out, trying a fresh install on it, and trying the same things that have been causing your current issue.  If everything works fine then it's likely the previous drive.

I know not everyone has a spare hard drive, but it's worth a shot.

Oh man, I hope that's not it. Unfortunately, it's a laptop, so I don't have another hard drive lying around.

Also, only one partition (hda6 below) is unmounting incorrectly. I have other partitions as well:

hda1: Windows partition
hda2: Documents partition
hda3: Pictures partition
hda5: Root partition
hda6: Miscellaneous partition

hda1 = ntfs, hda2 and hda3=fat32, hda5 and hda6=ext3

Further clarification: it's only new files that may get deleted, all my old files have been untouched, but a portion of the new ones disappear sometimes.

If this continues, I'll try a new install anyway.

---

### Post by tigerhawkvok on 2008-01-26
I actually have been having a similar problem.  My drive checks out as fine, and I also had tried a reinstallation.  Thankfully, the fsck has been finding and fixing errors, but it does have to go through a check on *every* boot after a shutdown.

---

### Post by se2131 on 2008-02-01
Following up: basically I was an idiot. I have my computer set up as a dual-boot w/ Ubuntu and Windows XP. I was hibernating XP, which of course writes to disk, and later booting into Ubuntu, and then back into XP, etc. etc. Basically things were getting overwritten I guess from doing this hibernating stuff.

---

