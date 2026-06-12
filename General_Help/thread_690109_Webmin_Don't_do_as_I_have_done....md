---
title: "Webmin: Don't do as I have done..."
date: 2008-02-07
forum: General Help
---

### Post by Zack McCool on 2008-02-07
All right, after reading about it here (and in Usenet) several times, I installed webmin on my machine a few weeks ago.  Thought I'd give it a whirl.

I like it.  It has a good interface, and it makes it very easy to get things done.

Sometimes too easy, though.  Here is a word of warning:  

[SIZE="5"]Be VERY Careful with the partitioning tool in Webmin.[/SIZE]

Using the Hardware | Partition Manager, you can easily delete or create partitions on your disks.  BUT, Webmin does not check to see if they are currently mounted, and will remove them even if they are.  Also, after removing a partition, webmin re-numbers the remaining partitions to fill in the blank, meaning that if you are mounting using /dev/sdx instead of UUID's, you will have to reconfigure your fstab.

The other day, I wanted to remove a few partitions that were no longer in use (from Feisty) on my hard drive.  Some were in the Extended partition, so gparted wouldn't do it without unmounting all the other partitions in the Extended area.  Webmin would, though.  And once it removed one, it renumbered the others, and no longer showed them as mounted.  I was removing them by the partition numbers, and didn't notice they had changed.

I ended up deleting /, /var, /tmp.  I had ample backups to do a reinstall, and get everything working again fairly quickly, but it was a frustrating experience.  Just wanted to let newer users know, so they don't make the same errors as a guy that has been working with (Administering) linux for several years.  And, please, backup your data regularly.  You never know when you'll need it.

---

