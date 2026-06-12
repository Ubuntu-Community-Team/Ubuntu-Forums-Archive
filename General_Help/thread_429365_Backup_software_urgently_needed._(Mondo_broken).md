---
title: "Backup software urgently needed. (Mondo broken?)"
date: 2007-05-01
forum: General Help
---

### Post by whitefort on 2007-05-01
Hi.

It's crucial to me that I can regularly do full system backups of my Ubuntu machines.  With Dapper, I've been using a superb program called Mondo.  It creates a backup which can then be used either to restore individual files, or to do a full 'bare metal' restore of the system exactly as it was at the time of the backup.

The problem is that I've switched to Feisty - and Mondo doesn't seem to work with Feisty.  The backup still seems to go OK, but then totally fails to restore. (actually it trashes the system when it tries) Not very useful!!

I would really prefer not to have to roll all my machines back to Dapper but that's what I'll have to do unless I can find a mondo replacement.

I would be REALLY grateful if anyone can recommend an alternative program that will do this sort of total 'disaster recovery' backup for me.

(Also, how does one go about reporting that the repository contains incompatible software?  if anyone's using Mondo for really important stuff they could be in for a serious shock.  Non-functioning backup software is one of the most critical flaws I can think of.)

Many thanks!

---

### Post by strabes on 2007-05-01
Try sbackup. It's in the repos.

---

### Post by whitefort on 2007-05-01
Thanks.

Sbackup seems to be OK for backing up files and directories, but what I'm really looking for is something that, in effect, makes an image of the hard drive and puts it on a bootable CD/DVD.

With Mondo, even in the event of a total hard drive failure, it's possible to replace the drive, insert the DVD, and in a very short time have the system exactly the way it was before the failure.  Obviously hard drive failures aren't common, but I do like to know that even in the event of something happens that leaves my system in an unbootable state (as some Ubuntu updates have done!), I can get up and running again quickly.

Is there anyway to offically report that the Feisty Mondo is broken and request a fix?

As I say, non-working disaster recovery software is a bit of a... disaster!

Thanks

---

