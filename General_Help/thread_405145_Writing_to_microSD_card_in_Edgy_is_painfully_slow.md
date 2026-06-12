---
title: "Writing to microSD card in Edgy is painfully slow"
date: 2007-04-09
forum: General Help
---

### Post by rrwo on 2007-04-09
Apparently microSD cards on my ThinkPad Z60m work in the internal card reader. Sometimes.  But when I write to them, the speed is initially acceptable but then slows down, to where copying a few MB takes minutes.  Sometimes the entire system's response time is slowed down, even though the CPU meter shows little activity.

Other times the cards just don't work at all.

Rebooting doesn't help. It might work, it might now.

Leaving the card in when booting causes the system to lock up until the card is removed.

Sometimes when I put the card in, it mounts, but I geta Failed to mount error.  Same problem when I unmount.

Sometimes when I unmount (even with no error), files I copied to the drive are not there!

I've just re-inserted the card after unmounting (no errors), but found that the files were missing (when looking on the card using my mobile phone).  I've got a failed to mount error, plus another failure error that says

[INDENT]Method "Mount" with signature "ssas" on interface "org.freedesktop.Hal.Device.Volume" doesn't exist
.[/INDENT]

But the card appears to be mounted anyway.

I've used fsck.vfat to reclaim lost clusters.

I'm at my wits end with this!

---

