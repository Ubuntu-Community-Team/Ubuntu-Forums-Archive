---
title: "File system corruption, ubuntu reports much less free space available than there is"
date: 2007-07-14
forum: General Help
---

### Post by Funzo22 on 2007-07-14
Okay, I upgraded my hard drive last week, and it didn't go too smoothly...

Well, when I upgraded my hdd from a 320gb to a 500gb, I simply used dd to clone my /home partition from the old hard drive onto the new hard drive, then I resized the partition to take advantage of the extra space. However, the resizing operation was where everything went wrong, it told me there was a problem and I may have lost all my stuff or something along those lines. But, after rebooting back to the livecd, all my stuff was still there, so I figured it was fine. I installed ubuntu, and set it to use my /home partititon as it should. But after starting ubuntu, it was crashing all the time, so I ran an fsck check on the filesystem, and it found loads of problems, however it repaired them all, and after that, my computer stopped crashing, and started going faster. But, now, my computer seems to report a lot less available space than there is.

My user is the only user, so I know that I am seeing accurate numbers. when I view properties of /home, it says that it takes up 228.5 gb of space, and when I go to gparted, it says the partition is 451.11gb, and that I have used 420.05gb, and there is 31.06gb left.

I am looking for a way of fixing this other than reformatting.

Thanks

EDIT: also forgot to mention that fsck comes up clean now after it repaired it

---

### Post by rillip on 2007-07-14
I think you may just be seeing the % of ext3 that's held back for the root user.

See this page for an example:

[http://boncey.org/2006_11_18_reclaiming_ext3_disk_space]("http://boncey.org/2006_11_18_reclaiming_ext3_disk_space")

---

### Post by HermanAB on 2007-07-14
Also remember that Ext3 wastes a huge amount of space for its journal - at least 7%.  A better file system such as JFS only uses 0.2% for its journal.  However, that being said, Ext3 is still tons better than NTFS which uses 12 to 20% of the disk for its journal.

---

### Post by Funzo22 on 2007-07-14
Thanks guys. but the ammount of space being wasted was nearly 200gb, but I solved my problem, I booted from the livecd and I resized the partition 1mb smaller, I guess it didn't finish writing some of hte info to the disk last time when I resized the partition, but now it works!

I now have 202.9gb free

Thanks

---

