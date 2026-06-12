---
title: "fsck fail died exit status 8 (solved)"
date: 2007-12-17
forum: General Help
---

### Post by Sbarton on 2007-12-17
Just thought I would post re solving the fsck problem I was having.
I have 7.10 installed on hda and decided to install also on hdb.After installing on the slave drive (hdb) I could not boot into Master (hda). After reinstalling 'Grub' on HDA I could not boot into the slave drive. At various times I got the fsck failure and had no success with the live CD or fsck. In the end I noticed a discrepancy in the UUID of the menu list on hda that was different from the menu list on hdb (slave drive). So I decided to change the UUID on the menulist on hda to correspond with the UUID on the slave drive. 'Viola' success.
I think there has been a problem with UUID's, anyway I am a happy bunny now!
Maybe it may help someone.
regards

---

