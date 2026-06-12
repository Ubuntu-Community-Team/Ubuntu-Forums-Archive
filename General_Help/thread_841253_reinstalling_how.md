---
title: "reinstalling how?"
date: 2008-06-26
forum: General Help
---

### Post by Smithben1983 on 2008-06-26
i have played with ubuntu all night and seeing that this is my first time i have decided that i want to start over but cant see how to do a fresh install, i tried from the live CD but it is trying to make me leave a small area for my first install and using the partition editor thing i cant delete the partition i made. also i still have windows XP on my comp and dont want to lose it. any ideas what i am doing wrong?

---

### Post by Elfy on 2008-06-26
At a guess not using the manual option - when you get to the partitioning part of the install choose manual.

You will get a new window which will show your existing partitions - you will have ntfs for windows and if you used the auto partition tool first time round an extended (probably) with an ext3 and swap partition.

Select the ext3 partition - then choose edit - in the newly opened window choose a mountpoint as / this will now be your new installation, the existing swap will be recognised and used again.

Do not touch the ntfs partition with the partitioner and it will be untouched by the process.

This will overwrite your existing buntu installation so you will lose anything you have there.

Hope that helps

---

### Post by ajgreeny on 2008-06-26
I assume from your post that you have already installed ubuntu once and now want to get rid of it and start again from scratch.  There is no need to uninstall or delete, just overwrite old with the new.

Firstly, why?  Do you need more room for ubuntu, or less.  You must have managed once to install without wiping windows from your disk so you know it is possible, and have done it.  So if you want to keep the same size partitions just overwrite the current ubuntu partitions with the new install.  When the installer gets to partitioning, chose Manual (or custom, I can't remember how it's described) and pick the partitions used for the first ubuntu install to use for the second one.  For ease you only need to worry about two partitions, one for root (/) and a small one of about 512MB - 1024MB for swap.  If your windows is a single partition, then ubuntu probably installed itself into sda2 (or hda2, depending on disk type) and swap into an extended partition, probably sda3 within which is a logical partition sda5.  Logical partitions always start numbering from 5 up, as primary partitions can be up to 4 on a disk.

Don't worry too much about that, and before you reinstall, run partition editor from the live CD to check out which partition is which.  One will be ntfs, or maybe fat32, and that will be windows.  One will be ext3, your old ubuntu install, one may be extended and that may contain your linux swap, or the swap may just be a primary partition depending on how you installed last time.  Make sure you chose the old ext3 partition for your new / partition and the old swap for the new swap and all should be fine. Whatever you do make sure you have no check marks in the ntfs or fat32 partition rows for formatting those or you will lose windows.  Lastly, though it should have been first, BACKUP, BACKUP, BACKUP.   You know it makes sense!

EDIT  OK, too slow for Forestpixie2

---

### Post by Elfy on 2008-06-26
heh heh heh - you always seemed to beat me before I was the new improved MkII version :)

---

