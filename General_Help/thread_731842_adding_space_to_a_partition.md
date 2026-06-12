---
title: "adding space to a partition?"
date: 2008-03-22
forum: General Help
---

### Post by eheyl on 2008-03-22
I did post about this that was in october of last year still have the same issue (got busy) so thought I'd repost. Here's a pic of my partitions. Basically I want to plunk the sda6 partition that is currently on the right of the unused 18gb sda3 partition to the left of it and add it.So I want to add the 18gb of free space to the remaining 1.9 gb of space on sda6.  I've been playing with the livecd gparted and can't figure out how to do this, unless I've goofed it up and can't. I'm honestly stumped and would love some help.

---

### Post by ryanhaigh on 2008-03-22
I think the easiest thing would be to move the data from sda6 to sda3, then delete sda6 and resize sda3 to take up the space left by the deleted sda6.
As with any partiton operation you should backup first.

Edit:
Actually it is more complicated than that because you have an extended partition. So move data from sda6 to sda3, delete all partitions on the extended partition and the extended partition itself, then resize sda3 to your desired size and create a new swap partition, obviously this will all need to be done from a live cd and you will probably need to change your grub and fstab to allow for these changes.

---

