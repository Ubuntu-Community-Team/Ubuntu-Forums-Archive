---
title: "File mode and other details unreadable"
date: 2014-11-18
forum: General Help
---

### Post by James Wilde on 2014-11-18
I'm running 14.04.01 on a HP, and using a 3 TB usb disk, formatted as two partitions, 3TB1 and 3TB2 both with ntfs.

The data on these two partitions has got out of control and I'm tidying them up.  I've got 3TB2 nearly empty.  The only thing remaining is a directory called .Trashes, which, some way down has several directories with files for which the mode, owner, group, size and date are unreadable, and show as ?.  I have -????????? ? ?    ?       ?            ? Scene01.avi as an example of one file.  There are some directories with strange modes also.

I've tried formatting the partition, but this directory tree remains.  I've tried rm on a file, and even sudo rm, but it can't be removed.

Anyone seen this before, and even more important, has anyone managed to get rid of it?

TIA

---

### Post by matt_symes on 2014-11-18
Hi

> **James Wilde said:**
> I'm running 14.04.01 on a HP, and using a 3 TB usb disk, formatted as two partitions, 3TB1 and 3TB2 both with ntfs.

The data on these two partitions has got out of control and I'm tidying them up.  I've got 3TB2 nearly empty.  The only thing remaining is a directory called .Trashes, which, some way down has several directories with files for which the mode, owner, group, size and date are unreadable, and show as ?.  I have -????????? ? ?    ?       ?            ? Scene01.avi as an example of one file.  There are some directories with strange modes also.

I've tried formatting the partition, but this directory tree remains.  I've tried rm on a file, and even sudo rm, but it can't be removed.

Anyone seen this before, and even more important, has anyone managed to get rid of it?

TIA

Did you run an fsck both the partitions ? 

Use the -f flag to force a check even if the drive thinks it clean. This is important to do so if you don't know how to do this then post back.

That may help.

Kind regards

---

### Post by ajgreeny on 2014-11-18
I don't think you can use fsck on ntfs partitions, unless things have changed a lot.

It is always said that it's best to use a windows OS and utility to mend a broken windows (ntfs) partition.

---

### Post by matt_symes on 2014-11-18
Hi

> **ajgreeny said:**
> I don't think you can use fsck on ntfs partitions, unless things have changed a lot.

It is always said that it's best to use a windows OS and utility to mend a broken windows (ntfs) partition.

Yep. Missed the filesystem type on the original post.

ajgreeny, you are quite correct of course and thanks for it pointing out. Much better to stop mistakes early.

I'll go and get my eyesite checked :)

Kind regards

---

### Post by James Wilde on 2014-11-19
Thanks, guys, for helping out.  In the end I deleted the partition and recreated it - since it was empty of everything except the problems.

The reason this disks partitions are ntfs is that the drive was intended to be attached to the router, and at this size, ntfs was the onl easilyy shareable file structure which would serve my wife's windows box and my mac and linux boxes.  It turned out the router wouldn't recognize it anyway, so now it's attached to the linux box.  I suspect the reason the router wouldn't recognize it is that it has a guid partition system instead of mbr, but I'm not interested enough to experiment.  Its being ntfs means that I can always connect it to any of our machines directly and it can be read.

---

