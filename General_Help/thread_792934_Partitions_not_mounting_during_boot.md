---
title: "Partitions not mounting during boot"
date: 2008-05-13
forum: General Help
---

### Post by seanhogge on 2008-05-13
I have a problem that I'd like some direction on before I start getting crazy with attempted solutions.  I'll make this short, including only what I know for sure.

I'm running Xubuntu Hardy.

I installed the system with a USB hard drive attached.  Hardy correctly found it, added to my fstab, all was well.  I recently removed that USB drive, and I can only suspect that it has caused some odd changes.

My device files changed.  What was previously /dev/sdb is now /dev/sdc.  Which means the normal boot sequence halts, asks me for my password, then puts me into a recovery-console-like command line.

I altered my fstab to reflect these changes by removing the USB drive entry, and changing all the UUID entries to device file pointers.  However, the problem still occurs.

When it drops me out of the normal boot sequence, I do a quick "mount -a" and then "reboot" and the boot process continues (without actually rebooting).

It appears the boot sequence is attempting to fsck something right before it asks for my password for the command line.  Do I simply need to boot to a live CD and let fsck run on my partitions?  Or is there some deeper issue that needs to be solved to get back to a normal boot?

Also, if there is a thread that already addresses this problem, please point me to it.  I didn't find any with my fumbling searches.

Many thanks!

---

### Post by pointone on 2008-05-14
If fsck is failing, it usually requires you to run it manually. Once on the command line, simply manually fsck the drive it attempted to fsck during boot. 

Posting the exact error messages might be helpful for diagnosing the problem if this doesn't help.

---

