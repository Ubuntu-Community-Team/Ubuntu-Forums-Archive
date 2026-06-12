---
title: "Weird confusing problem solved"
date: 2007-01-29
forum: General Help
---

### Post by dwasifar on 2007-01-29
Earlier today I rebooted my Edgy box and when it came back up it seemed to have traveled through a time warp.   The first thing I noticed was I was missing all email from December 20th onward.  So I went poking around in the Thunderbird directory trying to see what was wrong, but there was nothing out of the ordinary.  Then I noticed my browser history was wrong too; and THEN it hit me that there were things missing from the desktop that I'd left there, and not only that, there were things that had RETURNED to the desktop that I knew I'd deleted.  

The first thing I thought was that I must have inadvertently created an alternate profile somehow and been working in it for a month.  I logged in as root and went, well, rooting around.  No additional profile, no extra directory in the home folder.

I was scratching my head.  How could all this stuff just revert spontaneously?

Then something occurred to me.  I looked in gparted, and sure enough, I found the problem.

I have a second hard drive installed in the system and periodically I use it to make a clone backup of the main drive.  The system drive is at /dev/hda and the backup is at /dev/hdb.  Gparted showed me an alert icon for /dev/hda1; looking at the error message I saw "Unable to find mount point."  What was happening, was that the system, unable to use /dev/hda, used /dev/hdb instead, booting to a backup made on 12/20.

I opened up a terminal and ran fsck; it recovered the journal and fixed a few orphans on /dev/hda.  One quick reboot later and everything was back to normal.

---

