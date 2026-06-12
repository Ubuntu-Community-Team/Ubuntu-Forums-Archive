---
title: "Gave up waiting for root device."
date: 2013-02-22
forum: General Help
---

### Post by robertVM on 2013-02-22
I have spend the last few hours looking at posts from people with similar problems. Unfortunately I don't see one that has a solution for me.

Here is what happened: Received a message that there was only 8.6mb of space left on the boot partition.
As the boot partition is locked during use I used a gparted disc to increase the size of this partition.
There were no error messages during this operation but when I restarted the computer, first of all I get the GRUB2 menu which I never did before this and after that it doesn't matter which of the installations (Regular, recovery or previous versions) I select I end up with the message:
Gave up waiting for root device. Common problems:
- a list of 4 common problems
!ALERT /dev/mapper/servername-root does not exist. dropping to a shell.

I tried everything I can think of - started the computer with a live CD - ran Boot - Repair and I am at a loss.
The resulting log from my boot-repair can be found at:
[http://paste.ubuntu.com/5556988/](http://paste.ubuntu.com/5556988/)

The computer has only one operating system and as far as I can tell the GRUB loader is pointing to the right files on the right disk-partition (SDD1)

Any help/suggestions would be greatly appreciated!!

Thanks,
Robert

---

### Post by ersatzsplatt on 2013-02-22
Sounds awful and I don't see any other replies ... so I'll give it my best shot.
I don't know how to give you the surgical advice that would be best.  ... I can suggest that you look at some kind of reinstall options.  You could reinstall on another drive and mount the drive you have; copy the files you want over ... like that.  Or live disk; mount the drive you have; copy the files you need to save to some other media; then reinstall on the same drive.
Of course you may be able to get better advice not requiring this kind of overhead ...

Good luck!

---

### Post by robertVM on 2013-02-23
Thanks, I think gparted destroyed the file system in my boot device. Pretty well disastrous; there goes my weekend :)

---

