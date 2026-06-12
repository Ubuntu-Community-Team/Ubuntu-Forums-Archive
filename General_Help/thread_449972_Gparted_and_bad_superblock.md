---
title: "Gparted and bad superblock"
date: 2007-05-20
forum: General Help
---

### Post by catdriver on 2007-05-20
So here's the situation:
I have a 60 gb disk, it had a botched upgrade of 6.06 Dapper.  I therefore went ahead and moved to Feisty.  To do so I shrank the existing partition containing dapper, because I have a large number of media files that were impractical to back up.  It went fine.  I ended up with a parttion on the front odf the disk with dapper and one on the tail with Feisty.  I mounted the old system and transfered the files over to my new partition.
    Comes time to eliminate the old parttion and resize the new one and find it's not possible to expand "upward" only "downward" on the disk.  No problem, I did the entire thing again.  Now I can remove the old partition on the back end of the disk and enlarge the new partition.  So far so good.  Boot up a gparted disk and make the change, *however* it appears that it did not or incorrectly wrote the new partition info the the superblock.  Now when I boot I get an error complaining about the bad superblock and I drop to a shell, I can cntr-alt-del out of the shell and boot up resumes normally.  Things seem ok, but some apps are hanging for no apparent reason except that I made the partition larger.  
  So I suspect I need to reformat eh newly sized partition, but then I'm faced with having to back up all those files that I'm trying not to have to burn out to CD. Is the the case or is there something I can do at the command line that will repair the bad superblock without losing my data? Failing that I will buy another disk and reinstall (yet  again and start over...) which of course brings to bear the SATA issue that seems to be a part of the current upgrade cycle.  As it is I can only run one HD and one CD drive and that's kind of a problem.....

02 22 2007....

simple things are sometimes hard to remember...
When I killed the second ext3 partition using a bootable gparted disk, I forgot that I had to manually remove it from my /etc/fstab.... that caused the boot sequence to brain fart and it crashed out rpior to mounting my CD drives, cleaned up /etc/fstab and it works again and there is no bootup lag.  So the ATA SATA thing is not an issue.

---

### Post by MoLE on 2007-05-21
I found the following [blog post]("http://ozdocit.org/tiki-view_blog_post.php?blogId=6&postId=17") which seems to walk through a similar problem - technique seems to utilise bootable CDs only.

HTH

---

### Post by catdriver on 2007-05-21
thanks for the link.. I'll give it a shot *after* I add a second HD so I can back up all that data I can't stand the idea of loseing.

---

