---
title: "dump for Ubuntu?"
date: 2005-04-08
forum: General Help
---

### Post by James_Ward on 2005-04-08
Hi,

I use ubuntu and backuppc to create a 1.5TB+ filesystem on a 7x250 striped array of USB hard drives.  I want to back this up (preserving all the hard links created by backuppc) to tape for offsite storage.  I see there's no dump command installed, but it appears to be available as a port from BSD 4.4?

Is dump the right thing to back up thousands of hard links to tape? (If so, how do I get it for ubuntu?)

Is there an installed tool that can handle the job?  (I heard tar breaks on this problem).

Thanks in advance,

James

---

### Post by Nickus on 2005-04-08
On my hoary machine I have dump in /sbin/dump. But I wouldn't really recommend backing up 1.5TB just with dump. A better way would be to use a real backup software llke Bacula (which exists as ubuntu packages). I don't know how well that handles hard links though.

cheers,
Nickus

---

