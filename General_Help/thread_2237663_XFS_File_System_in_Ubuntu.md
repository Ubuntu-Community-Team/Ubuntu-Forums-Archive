---
title: "XFS File System in Ubuntu"
date: 2014-08-03
forum: General Help
---

### Post by Canaryguy on 2014-08-03
Hello,

I have been reading about the XFS file system and I was wondering if this FS is in fact better than EXT4. Does anybody use this FS? I'm using a netbook with Ubuntu 14.04 x32 with Unity and I would like to know if the performance of the system would improve with XFS.

---

### Post by HermanAB on 2014-08-03
Short answer: Not so that you will notice.

I have tested various file systems on identical machines about a decade ago for a video server system used in hotels.  XFS and JFS were faster than Ext3.  JFS was actually the fastest (by about 5%).  I have not done any such tests on Ext4, but my guess is that XFS will be faster by 3 to 5%.  

However, the difference is not so much that you will notice anything on a run of the mill system.  If you really need speed, then get rid of the spinning rust and use a solid state drive - then you will actually notice a big improvement.

---

### Post by Canaryguy on 2014-08-03
Thanks HermanAB. I didn't expect too much improvement with the XFS alone.

---

### Post by nerdtron on 2014-08-03
Been using XFS on servers lately especially on mysql databases and on disks that handle thousands of small files. Seems to be stable enough, I didn't run any benchmarks though.

---

### Post by SeijiSensei on 2014-08-03
I found XFS quite fragile when it comes to things like power outages.  I had an external drive with XFS.  Anytime the drive lost power, I lost data.  As a result I would only use XFS on hardware with solid backup power.  I doubt you'll see much improvement over ext4.  I replaced XFS with ext4 on that external drive and saw no visible differences in transfer rates while streaming video from it.

---

### Post by zircon009 on 2014-08-03
I have been using xfs for around 6 to 7 years.  I have a large media file server for the entire time.  XFS has been good and stable in my environment, but I have always had a system monitored battery backup. Power failure can cause data loss. I briefly tried EXT4 with 64bit instead of the default 48bit option and ran into a bunch of bugs with the 64bit fs branch. I would only recommend use EXT4 with the default 48bit file system addressing.  48bit would also limit you to 16TB of total space. The only issue with XFS, is it tried to be to smart in file system creation.  I messed up and took the defaults once, and ended up with a million or so ags on a file system, instead of 16-32.  It would take days to check disk because of this.  Its best to specify your strip width and strip number when creating, to match your underlining hardware disk configuration.  Also you will probably need to check and defrag xfs occasionally.  It depends on how often you are writing and deleting to it.  XFS does not have a background defrag that natively runs, I just run a cron job late at night to do this.  The file system can still be mounted while it defrags. Also check disk operation on large xfs file systems can be a challenge, on the memory utilization aspect. The system will not check the disk on a x number of mounts either.  But XFS has been around for a long time, and is a very good file system for large file systems, as your choices are still quiet limited.  Seems like overkill for a root or smaller file systems, in my opinion, but i see other major linux releases are going to it. 

Later.

---

