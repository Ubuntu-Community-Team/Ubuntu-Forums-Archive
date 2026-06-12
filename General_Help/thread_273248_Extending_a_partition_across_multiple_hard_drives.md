---
title: "Extending a partition across multiple hard drives"
date: 2006-10-07
forum: General Help
---

### Post by Vertelemming on 2006-10-07
So, I've recently begun converting my computer from Windows to Ubuntu. To help move data over, I borrowed a second hard drive to store data on, so I could move userdata from the Windows partition off, resize the partition down, and then install Ubuntu in the free space. This worked fine, and so now my partition setup is something like this:

/dev/sda1 (primary nfts) mounted as /media/sda1
/dev/sda2 (primary ext3) mounted as /
/dev/sda5 (logical swap) mounted as swap
/dev/sda6 (logical ext3) mounted as /home
/dev/sdb1 (primary ntfs) mounted as /media/sdb1

Now, after all this had been setup, the person who lent me the hard drive has allowed me to keep it permanently. Which brings me to the point of this whole post.

Is it possible to extend the partition mounted as /home so that it will cover the free space on the first hard drive, and the free space on the second hard drive too, without losing the data that's currently on /dev/sda6? I've done some Googling, and it seems that either LVM or EVMS are what I want, but I can't find out whether it would destroy the pre-existing data, or a howto that I feel comfortable following on Ubuntu, so any help here could be appreciated.

---

### Post by louieb on 2006-10-07
Unfortunately I do not think there is a way of converting a regular partition to LVM on the fly. There may be something out there to do this but who knows how safe the data would be.
 If it were mine I would:
[list]
[*]Plan the new partitioning scheme.
[*]Backup my data
[*]Partition
[*]Install operating system and any other programs.
[*]Restore my data files from backup.  
[/list]  
I have gone through this a few times and believe me it is a pain in the a.. Sometimes it has been worth effort sometimes not.

---

### Post by Vertelemming on 2006-10-09
Hrm. Oh well. Thanks for the reply. I'll see what I can do about finding a place to backup all my data.

---

### Post by CatKiller on 2006-10-09
Well, it's not quite as funky a solution as you want, but you can always mount partitions on the new drive to directories in your home folder, /home/vertelemming/stuff, say.

---

