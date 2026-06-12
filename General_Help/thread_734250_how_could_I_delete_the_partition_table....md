---
title: "how could I delete the partition table..."
date: 2008-03-24
forum: General Help
---

### Post by Mia_tech on 2008-03-24
how could I delete the partition table on my hard drive..I've tried 
```
dd if=/dev/zero of=/dev/hda
```
to write a bounch of zeros to the drive but takes too long and the partition table it's very small I think that is not working....is there any way to wipe out the partition table

thanks

---

### Post by aaaantoine on 2008-03-24
What you've posted is a way to write zeros to every byte of the drive.  So yeah, that'll take a while.

Why don't you use gparted to delete all the partitions?  And *then*, if you're discarding or giving away the drive, use the dd command (or better yet, [shred](http://linux.about.com/library/cmd/blcmdl1_shred.htm) *{PS: Nevermind, I didn't RTFA; shred doesn't work well on journaled file systems, including ext3}*).  If you're keeping the drive, you can just use gparted to change the partition layout.

Is there a particular reason why you're targeting the partition table?

---

### Post by louieb on 2008-03-24
your so close. to overwite the MBR and the partition table.
```
dd if=/dev/zero of=/dev/hda  bs=512  count=1 
```
[Learn the DD command - LinuxQuestions.org]("http://www.linuxquestions.org/questions/showthread.php?t=362506")

---

### Post by Mia_tech on 2008-03-24
> **aaaantoine said:**
> What you've posted is a way to write zeros to every byte of the drive.  So yeah, that'll take a while.

Why don't you use gparted to delete all the partitions?  And *then*, if you're discarding or giving away the drive, use the dd command (or better yet, [shred](http://linux.about.com/library/cmd/blcmdl1_shred.htm) *{PS: Nevermind, I didn't RTFA; shred doesn't work well on journaled file systems, including ext3}*).  If you're keeping the drive, you can just use gparted to change the partition layout.

Is there a particular reason why you're targeting the partition table?

the reason been is I want to backup my windows and ubuntu machines with partiamge, but before I go live on doing that I'm testing partimage on my vmware server, so no danger yet, I'm backing up and restoring the partition image of my vmware machines ;O)...by the way I backed up the partition table with
```
dd if=/dev/sdo of=/file/mbr bs=512 count=1
```
and then I restore it with
```
dd if=/file/mbr of=/dev/sdo
```
and rebooted the system but I get: "error loading operating system" I'm guessing something went wrong with the restoring of the partition table, or am I missing something, I'll appreciate if someone can point me to the right direction 
ohh, and I'm using systemrescuecd for backing up and restoring the image

thanks

---

