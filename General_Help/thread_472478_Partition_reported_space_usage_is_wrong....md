---
title: "Partition reported space usage is wrong..."
date: 2007-06-13
forum: General Help
---

### Post by gwilson on 2007-06-13
I am at the point where I can't claim to be a newbie, but I do outsmart myself from time to time and mess things up. If you're a hard drive guru, please lend a hand.

I had a 20 Gig hda1 partition with another unused 20 gigs behind (above) it on the hard drive. I tried everything I could to resize it with Gparted while running Feisty off the very partition I was messing with, and then by running Feisty off a Live CD in the cdrom drive. When running off of the live cd, Gparted would begin to resize the partition but immediately give an error. Then I loaded the SAM 2007 live cd. At one point, I opened the "INSTALL" icon on the SAM desktop which took me to a disk partitioning program that allowed me to resize the hda1 partition by dragging it out to a full 40 gig. Whoops...

When I rebooted into Feisty 7.04, there was an error message because the partition had changed, but I was able to bypass that, and everything loaded normally. Here's the problem: When I started out, I had a 20 gig partition with about 12 gigs used up and 8 gigs empty. Now Gparted shows that I have 40.97 gig partition of which 25.68 gigs are used and 15.29 gigs are open.

Important: the other partition on this drive was not affected ina any way by all of this. The problem is in the partition rather than the drive, I guess.

Somehow, I screwed up size of the segments or something. Is there some sort of command line program that will do a thorough disk check and repair some or all of the problems? I'm not sure if there really is a problem with the segment size or (more likely) an error in the reported usage statistics for that partition. I'm hoping that a thorough diagnostic of the partition a la Norton Disk Doctor might straighten things out.

Any ideas? I'd appreciate the help.

Glen

---

### Post by gwilson on 2007-06-13
I dug myself out of this hole by booting up the Gutsy (7.1) live dvd and then resizing the damaged partition to a new size. Gparted seems to have run fsck and repaired all of the problems in the partition.

The real lesson I learned (once again) is that you should never panic and reinstall your system without checking out the possibilities. With Ubuntu Linux, there is usually a way to salvage your installation and set things right.

---

