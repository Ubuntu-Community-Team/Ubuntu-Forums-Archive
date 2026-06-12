---
title: "Filesystem Errors"
date: 2007-01-14
forum: General Help
---

### Post by Jammerwoch on 2007-01-14
About a month ago, I logged into Trac (an apache-based project management server) on my Ubuntu server only to receive rude messages about being unable to create temporary database files.  I logged on, only to find that parts of my filesystem were mounted as unreadable.  Not knowing what else to do, I rebooted, and was informed that there were problems with my filesystem and I would have to run fsck manually, which I did.  There were a lot of errors, all of which fsck fixed.  So far so good.

But then it happened again, today.  This is worrisome to me -- this is a critical system and I'm using Linux for reasons of reliability.  What if the errors can't be recovered from next time?  Even if it's always recoverable, this is a huge nuisance at best.

Some helpful info: all of my filesystems are mounted on a cheap SATA RAID controller.  It's two identical drives with RAID 1 (mirroring).  I've got clean power being run through a hefty UPS system, so I'm pretty sure the drives aren't being subjected to any ugly power spikes.  uname -a gives:

Linux nibbler 2.6.15-26-386 #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006 i686 GNU/Linux

Here's what I want to know:
 * Is one (or both) of my hard drives failing?
 * Is there a log somewhere that will tell me why the filesystems were re-mounted read-only?
 * Is there any way to get more information so I can correctly diagnose this problem.

Any information would be welcome.

Best,
  Todd

---

### Post by kebes on 2007-01-14
Well whenever I've seen drive errors that keep appearing after subsequent reboots, it's been the hard drives that were the problem. If this is an important server, then I would not take the chance (or waste time)--I would immediately replace the hard drives.

You can look through "/var/log/" and see what the logfiles say. "syslog" or "messages" might have an error report.

---

