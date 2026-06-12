---
title: "How to Back Up/ Clone Entire Harddisk on dual Booted System?"
date: 2014-06-05
forum: General Help
---

### Post by asiancraig2 on 2014-06-05
I have an inspiron 1520 with windows xp and ubuntu on it.  How do i back up or make a clone of the entire hard disk?  i don't want to copy just one partition, but the entire Hard disk with both OS on it and the boot order of the Operating systems, basically make a ghost  copy.   I want to be able to take the newly cloned harddisk, and plug it in immediately after the process, and still be able to to both both OS and everything without any hassles.

What are some good programs to do this?  the program can be for linux or windows, but preferably for windows XP.  Thanks.

---

### Post by sudodus on 2014-06-05
I would use ***Clonezilla*** for that task.

[http://clonezilla.org/](http://clonezilla.org/)

Run this program from a live CD/DVD/USB drive and clone from the source drive to a target drive of at least the same size.

Many people (including me) use Clonezilla to create a compressed image instead of a direct clone. This will reduce the size a lot, but you have to expand it to a target drive of at least the same size in order to use it, which might take an hour or two (very much depending on the amount of data and the speed).

---

### Post by asiancraig2 on 2014-06-05
> **sudodus said:**
> I would use ***Clonezilla*** for that task.

[http://clonezilla.org/](http://clonezilla.org/)

Run this program from a live CD/DVD/USB drive and clone from the source drive to a target drive of at least the same size.

Many people (including me) use Clonezilla to create a compressed image instead of a direct clone. This will reduce the size a lot, but you have to expand it to a target drive of at least the same size in order to use it, which might take an hour or two (very much depending on the amount of data and the speed).

If i take the compressed cloned disk using clonezillla and put it back into my computer, it will boot up the same as with with original dual booted hard disk with grub on it?

---

### Post by Mark Phelps on 2014-06-05
The compressed image is a file (or actually, a set of files) whose only purpose is to be used to restore the original disk.  IT can't be mounted and it can't be used as a filesystem.

If you "clone" the original disk to another disk of the same size or larger, then you could swap the disks and boot from the "clone".

---

### Post by sudodus on 2014-06-05
> **asiancraig2 said:**
> If i take the compressed cloned disk using clonezillla and put it back into my computer, it will boot up the same as with with original dual booted hard disk with grub on it?

The compressed cloned disk image must be expanded and does *not* run 'as it is'.

> **Mark Phelps said:**
> The compressed image is a file (or actually, a set of files) whose only purpose is to be used to restore the original disk.  IT can't be mounted and it can't be used as a filesystem.

If you "clone" the original disk to another disk of the same size or larger, then you could swap the disks and boot from the "clone".

+1

It it is important that you can run directly, then ***clone*** the disk as adviced by Mark Phelps.

---

### Post by kakashi_12 on 2014-07-06
I've been using CloneZilla for a few years now and love it.
I've only seen 2 faults with this free program though.
1. It (along with Linux) won't see SATA III (aka 6 GB Sata cables) drives, for whatever reason.
2. I've never gotten "clone whole drive" to work well. I've always used the "Clone single partition" option. And it's worked terrifically.
Although, I probably have an older version of CloneZilla guessing and haven't updated. Maybe they've addressed these issues since then, who knows.

---

### Post by sudodus on 2014-07-07
I have no problems cloning a whole drive. Try the current stable version of Clonezilla.

---

### Post by Bucky Ball on 2014-07-07
Love Clonezilla. Here's some links that might help you get your head around it:

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

---

### Post by pretty_whistle on 2014-07-07
Redo Backup is another good one.

---

