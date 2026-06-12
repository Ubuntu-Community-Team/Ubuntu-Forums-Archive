---
title: "Overlapping Partitions"
date: 2007-06-30
forum: General Help
---

### Post by floguy on 2007-06-30
Recently I unfortunately had to install windows on another partition.  So I booted into feisty livecd, ran gparted to shrink my ext3 partition, and then installed windows into the unpartitioned space.

Turns out something must have gone wrong, because windows works fine, but booting to the livecd again to repair grub and get dual booting working revealed something bad: my partition table lists two partitions as overlapping.

I've read through:
[https://bugs.launchpad.net/ubuntu/+source/parted/+bug/9440](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/9440)
[https://bugs.launchpad.net/ubuntu/+source/parted/+bug/103794](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/103794)

It looks like using sfdisk is my best bet, but after reading the manpage on sfdisk, it seems like I should know what I'm doing before I do so.

I've attached my output of `sudo sfdisk -d` as the file partable.txt.

What do I do now?  Any and all help would be GREATLY appreciated!  Thanks in advance!

---

