---
title: "erase partition"
date: 2008-02-27
forum: General Help
---

### Post by grumpylad77 on 2008-02-27
I am dual booting Vista and Gutsy on my laptop. Now that I have wireless working in Gutsy, I want to wipe out the Vista partition. Is there any way to do that without re-installing Gutsy? Or will I have to re-install?

---

### Post by astrotech226 on 2008-02-27
There's a few ways to do this, but it's dangerous if you do anything wrong.  Be certain to back up anything you want to keep!

An easy way is to use fdisk.  You can delete the Vista partition and add one back.  Or you can just change the type from ntfs to Linux.  Then create a filesystem on it and mount it somewhere like "/new_partition".  The problem with this is that your available drive space is not all in your / partition which is most likely what you want.

So you'll need to read up on parted.  In theory, you can delete the Vista partition, move the Linux one to the beginning of the disk and then extend the partition to use the whole disk.  You'll then have to extend the filesystem to use the rest.   This option is considerably more dangerous to perform and great care should be taken.

There's probably other ways of doing this with LVM.  But much of this depends on your installation.

---

### Post by grumpylad77 on 2008-02-27
thanks astro helped a lot

---

### Post by astrotech226 on 2008-02-27
No problem!  If you detail a little bit about your partitions, I or someone else can probably give you the commands or procedures to get you pretty close.

---

