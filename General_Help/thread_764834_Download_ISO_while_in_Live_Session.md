---
title: "Download ISO while in Live Session?"
date: 2008-04-24
forum: General Help
---

### Post by jaymz168 on 2008-04-24
Hello all, need a little help here.  I screwed up my regular install something good (I can't get any network devices working again) and I want to reinstall.  I have a disk of Ubuntu 7.10 running a live session on my machine, and whenever I try to download the 8.04 image, I run out of diskspace.  Now, I've got an empty 4 gig partition and a half-empty 30 gig partition.  Given that the 'Live Session User' does not have permissions to write to either of these, how can I download that ISO to one of these partitions?

I don't want to install 7.10 just to run a dist-upgrade.  I would like to do a fresh 8.04 install.  Thanks guys.

---

### Post by Monicker on 2008-04-24
Try remounting one of the other partitions in read/write mode.


sudo mount -o remount,rw /media/otherpartition

---

