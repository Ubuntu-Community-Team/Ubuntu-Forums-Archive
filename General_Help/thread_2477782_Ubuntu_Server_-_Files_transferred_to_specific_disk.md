---
title: "Ubuntu Server - Files transferred to specific disk suddenly corrupt"
date: 2022-08-07
forum: General Help
---

### Post by cthog on 2022-08-07
Hi Everybody,

I have an Ubuntu home server (16), on an old Dell r710, which has been chugging away merrily for several years.  It has 6 disks (JBOD), all of which are mounted.  In the past week or so, I've noticed that video files transferred from one disk (let's call it Disk A) to another (Disk B) are all corrupted.  I've run cksum on the working file, then transferred to the suspect disk B, and received a different cksum result.  I've transferred to another Disk C, and file is correctly transferred (same checksum).  For some reason, I thought it would be a good idea to use BTRFS (just to be cool), in case that makes a difference.  So it appears that, all of a sudden, files transferred to Disk B (not over a network, all on same system) aren't copying correctly.  I'm currently running a health check on Disk B (btrfs scrub), but it hasn't found anything so far.  I'm not evern sure how to start troubleshooting, does anyone have any advice?

Again, this problem only started occurring about a week ago, it's been fine for years.

--Chris

---

### Post by TheFu on 2022-08-07
I don't use brtfs, mainly because there are many caveats about using it to above file corruption.  The modes you describe would only be an issue of the file system is extended across different disks.

It is also possible that the data path to partition B is fairing due to hardware issues.  That could be a bad cable, failing HBA port, failing HBA or a bad disk.  SMART can help diagnose some of those things.  Have you tried replacing partition B with another physical device? That would eliminate one of the most common failure points - the drive.

Also, don't confuse drive and partition.

---

