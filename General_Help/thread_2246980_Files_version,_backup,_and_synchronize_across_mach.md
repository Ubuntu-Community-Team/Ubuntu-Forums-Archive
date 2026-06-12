---
title: "Files: version, backup, and synchronize across machines"
date: 2014-10-04
forum: General Help
---

### Post by b00n on 2014-10-04
I have N machines and want to synchronize them often, want them backed up,  and want to be able to recover recently-deleted files.

The machines all use Ubuntu, so I am happy with an Ubuntu-specific or Linux-specific solution.

"Synchronize them often" means I am sitting at my desktop, then want to grab a small/light laptop and head out the door and have with me pretty close to a recent version of the disk.  I have been using Unison, but (a) it is manual, and (b) it needs to scan everything to sync, so is slow; but if I run it on a timer, the busy-work to scan and re-scan the disk interfers with local disk performance.  Better would be a mechanism that watches the file system, notes changes as I make them, and tries to "dribble" the changes over to the laptop (if it is on).

I want the above to work without a web/cloud, just a local connection between the machines.  For example, I am out wandering around taking photos with a camera and making notes on a tablet, when I get back to the car I can sync up with a laptop (more screen/memory/storage) without needing a web connection.

File versioning is great.  I have used snapshotting systems that run every (say) 15 minutes.  I've used non-Linux file systems that keep N backup copies of stuff automatically, which is even better for some kinds of oopsies (spent 10 minutes editing a file then deleted it by mistake).  I understand ZFS basically lets you say "show me what the file system looked like at time X" which seems even better.

Finally, I'd like to be able to do backups to several devices -- e.g., I am traveling for several days and want to back up to a USB hard drive, and capture as much of the versioning info as possible.  When I get back to home, do backups there.  I want to keep some USB drives at a few friends' houses, so if my home backup drives get stolen, I still have something semi-recent.

I realize solving all these things involve some Very Hard technical problems, but it seems like the individual ones have some pretty good approximate solutions.  For example, the general problem of doing resolution between two file systems is hard.  On the other hand, Unison does a "good enough" job for me.  Occasionally I have to do a manual merge, but that is rare so I am happy with it  Similarly, versioning systems tend to run out of space if unchecked, but I tend to create only .o files that are actually .o files, so a simple "delete at will" pattern for these things works well for me.

I'd appreciate it if folks can point me at a tool -- or several to use in combination -- which can help me with the above.  I am happy to use ZFS, etc., to solve the versioning part of the problem -- but it does not solve synchronization, and I do not know if there is even a way to synchronize the "time warp" data.  For example, if I create then delete a file on the Ubuntu tablet under ZFS, I would like to be able to see that on my laptop/desktop same as I could see it on the tablet.

This seems like it should be a well-worn discussion, but I poked around a bit and do not really see anything even remotely close.  So if y'all can help me out, I do appreciate it.

---

### Post by b00n on 2014-10-04
Maybe a simpler way of saying it is I always see the same view of (say) /home/$USER no matter which machine I used last and no matter which machine I use next.

Plus I want backups and a versioning file system.

And if something goes wrong (I used a machine then switched it off before synchronization finished) there should be some resolution protocol, like Unison, and not something like silent data corruption or a broken file system.

It is fine with me if these are provided with separate tools, but some things seem like they overlap -- e.g., the ZFS versioning looks to be hidden from Unison, so if I edit one file several times then synchronize with Unison, the new system only sees the latest version of the file, not any of the versioning.

---

