---
title: "ddrescue"
date: 2013-03-22
forum: General Help
---

### Post by ccw127 on 2013-03-22
I have a failed Seagate 1.5tb hard drive that I am trying to recover data from. I used ddrescue but ran into one (Possibly two) problems.

Possible problem: after about 50 gigs the drive died and I had to power cycle the drive. When I restarted ddrescue, it ran through almost 200 gig in only like 15 seconds (obviously not recovering anything). Is this normal? Could it be that those 200 gig really were bad sectors?

Issue 2:
The replacement drive is the exact size of the old and for some reason I ran out of room on drive (possibly because I was imaging a NTFS partition to a regular file on a ext3 drive). Now I can live with loosing the tail end of the drive, likely a small amount of data, but I want to make another pass on the drive to try for splits and hit the bad sectors again. Drescue won't seem to let me. Even if I give a specific start point in the middle ddrescue still drops out immediately complaining of no room on destination. Ideas?

Completely unrelated: I was trying to make this post using the mobile site, but it kept complaint that no prefix was selected... Only other there was no way to select a prefix on the mobile page. Is this a common problem?

---

