---
title: "gparted segfaulted - now booting with error:22"
date: 2008-06-05
forum: General Help
---

### Post by muszek on 2008-06-05
Long story short: I'm doing a over-the-voip family pc support gig.  There were 3 partitions: windows one, ext3 mounted as / and ext3 mounted as /home.  Task: give the 3rd partition back to windows world (re-format as ntfs and move /home to 2nd partition).

We managed to offload stuff from /home to the 2nd partitiona (removing the entry from /etc/fstab on the way).

Now, gparted was ran.  Format as NTFS.  OK, one pending job.  Device -> set label.  msdos type was chosen and "next" was clicked one or more times.  gparted segfaulted and when we ran it again, all partitions were gone.  We rebooted... and saw a blank screen with "error 22".

I have a livecd with dapper and hardy is being downloaded.  The installed realease?  I dunno, somewhere around feisty I guess.
We've ran gparted via dapper livecd.  It shows no partition and 74.53  GB (full disk) of unallocated space.

How do I proceed?  What could be broken?  Is it recoverable?

---

