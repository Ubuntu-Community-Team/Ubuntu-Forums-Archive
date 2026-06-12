---
title: "How to copy data over from an unbootable HDD?"
date: 2012-11-29
forum: General Help
---

### Post by Sirius3 on 2012-11-29
Let me preface by saying I'm very new to Ubuntu. I was informed using Ubuntu could help people who didn't have a  backup  image to restore to. That's essentially the information I'm looking for.

I'm using it to get my  most important files  off of my HDD that blue screened the other day.  It's been stuck in a  startup loop that can't fix itself. The HDD itself is fine. It passed  the windows memory diagnostics and hardware diagnostics. It also passed  the SMART tests even though it's still vague to me what that means. It  seemed relevant however.

From this I deduced it was simply an OS problem. My idea then was to copy most of my HDD data on to an external HDD,  wipe the old drive, reinstall windows, paste the information back onto the original HDD, and hope that everything works as it did before this issue.

Does this seem like a plausible plan? Are there other more efficient ways to do it?

---

### Post by SeijiSensei on 2012-11-29
Yes and no.  It's pretty much impossible to copy over programs in Windows because of their tight integration with the Registry.  You will probably have to reinstall any programs after rebuilding the hard drive.

As for your data, you can boot from the Ubuntu CD, choose "Try Ubuntu", and you will be able to mount and access your Windows directories.  You might be better off with a distribution designed to fix problems like yours,  Take a look at [Knoppix]("http://knoppix.net/") or the [SystemRescueCD]("http://www.sysresccd.org/SystemRescueCd_Homepage").

---

### Post by Mark Phelps on 2012-11-29
> **Sirius3 said:**
> My idea then was to copy most of my HDD data on to an external HDD,  wipe the old drive, reinstall windows, paste the information back onto the original HDD, and hope that everything works as it did before this issue.

Does this seem like a plausible plan? Are there other more efficient ways to do it?

Basically -- NO.  MS Windows puts app-related stuff into several different locations, including the registry which is actually a collection of files.  Finding all those places, copying off the files, and trying to recover the registry settings is all but impossible.

If this was a Win7 problem, you might try checking a a Win7 forum (sevenforums.com) to see if they can help.

---

### Post by efflandt on 2012-11-29
If something is corrupted or unreadable, cloning that to another drive by any means is likely to act just as it is now.  Many Linux tools will refuse to do anything with Windows partitions that show signs of not working properly.

So the best thing to do would be to put the drive in another computer that has Windows, or an external USB enclosure, and first see if Windows chkdsk /f can fix it, and then virus scan it.  If you are lucky, that might be all it needs (for now).  But drives normally keep some space that they automatically transparently remap in place of bad sectors, so if you actually start seeing bad sectors, that is a bad sign that the drive can only get worse.  Although, in one case doing those 2 things (chkdsk /f and virus scan) restored an infected drive that Windows had refused to boot.

There are tools like testdisk that can attempt to recover files even if partitions have been removed or altered.  But if that cannot figure out what the partitions were, the part of the disk that stores partition data is bad, or it cannot determine actual file names (even if it can deduce file types), you are very unlikely to end up with a bootable system.

In some cases of mechanical or electronic failure you might not be able to recover anything, without paying someone with a clean room and proper equipment a lot of money.

---

