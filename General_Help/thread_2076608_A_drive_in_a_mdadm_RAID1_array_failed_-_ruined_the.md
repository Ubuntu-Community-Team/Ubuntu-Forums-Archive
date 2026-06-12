---
title: "A drive in a mdadm RAID1 array failed - ruined the array?"
date: 2012-10-26
forum: General Help
---

### Post by Roasted on 2012-10-26
I'm curious if anybody can piece together some degree of logic to my story. My server is running 12.04, and it has 3 drives installed.

160GB = OS
2x500GB (RAID1 Mirror via mdadm) = /media/NAS

I noticed the files on my web server were gone one day, yet Apache was responding properly. I came home to find that Disk Utility reported one drive as healthy and the other as having "a few bad sectors." These drives are Seagates, and between the 2 I've already had 3 RMA's... this one marks the 4th. Anyway, I didn't know what to do, so I kicked out the problematic drive out of the array with the intention of running a degraded setup while I RMA'd the drive.

On a hunch, I re-added it. It took 2 hours to sync, but once done, it was fine. The following day I was going to be leaving for 10 days, and I just got back Tuesday. So we're talking ~2 weeks that it's been running problem free, despite Disk Utility reporting the SMART data as having a few bad sectors.

I know there's nothing to really fix now, but I can't help but to question, how on earth did a faulty drive manage to make ALL data on /media/NAS inaccessible UNTIL I removed it and re-added it and let it sync through? Isn't that the point of RAID? Redundancy? A drive failing in a redundant setup and therefore ruining the ability to use the data in the array doesn't make much sense.

Was this likely a fluke thing? Or does anybody else have a "me too" story out there to share?

---

