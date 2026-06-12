---
title: "how to fix bad sectors of  any hard drive?"
date: 2015-06-14
forum: General Help
---

### Post by thomas52 on 2015-06-14
i have been using my pc by dual booting ubuntu and windows 7 home basic, i have some doubts reguarding bad sectors shown by inbuilt disk application on my ubuntu 15.04 , can anyone please help me how to understand this error and how should i fix this issue? please refer the attachments and help me, thanks in advance.

---

### Post by Steve_Horan on 2015-06-14
Natively Ubuntu cannot correct NTFS partitions. You will need a 3rd Party tool.

> sudo apt-get install ntfs-3g

You can then run ntfsfix /dev/sda1 to correct your back blocks.

---

### Post by Vladlenin5000 on 2015-06-14
A few comments regarding your issue and post #2 which misses the target for miles...

1. Bad sectors cannot be corrected. The best any system can do is to mark those sectors as unusable. Their appearance indicates the drive is old and probably about to fail. Consider backup ASAP and replacement.
2. Bad sectors has nothing to do with file systems. It's a hardware problem, not software. As such, the comment about correcting NTFS partitions and installing ntfs-3g (which incidentally is installed by default) doesn't apply. the ntfsfix is limited to mark a given partition as needing error correction. Use Windows tools to correct logical (software) error in NTFS partitions; Windows tools cannot correct bad sectors. Like any similar tools it just mark them as unusable.

---

### Post by efflandt on 2015-06-14
Drives reserve some space to automatically remap good sectors in place of bad sectors regardless of OS. But I have never used that Disks app before, so it is not clear whether the drive already remapped those sectors or if those sectors are actually being used. It generally only becomes a problem when all of the error sites are used up and you actually start seeing bad sectors, because then it can only get worse.

When the Linux partition at the far end of my drive started getting bad sectors it became apparent when I suddenly had no permission to write to my home directory, because when Linux noticed the problem it remounted the partition read-only. I was able to nurse it along for a while using an e2fsck option to lock out badblocks from my backup system on SSD, but when that became too frequent I replaced the drive. I cloned my Win7 partitions, installed Ubuntu fresh, and copied over my home directory from the failing drive. The only corrupted files that I know of were a few Steam game files which checking integrity of game cache found and replaced.

---

