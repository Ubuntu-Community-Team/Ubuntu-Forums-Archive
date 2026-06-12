---
title: "Filesystem root running out of disk space"
date: 2015-04-13
forum: General Help
---

### Post by buzzcook on 2015-04-13
I'm running 64-bit Ubuntu 14.04 LTS, upgraded about a year ago. Recently I keep getting error messages when logging on that root is running out of disk space, e.g. today:
The volume "Filesystem root" has only 260.1 MB disk space remaining

I recently (2 weeks ago) use Gparted to add 5 GB to the root filesystem but apparently it's filled up again really quickly - no idea why

I've done all the usual things like Bleachbit, emptying trash for my user and for root, and cleaning out old packages.

Another confusing thing is that Gparted is reporting that I still have over 1 GB of free space - see attached screenshot.

See also attached output of sudo du -sh.

Any ideas what is going on here?

---

### Post by Holger_Gehrke on 2015-04-13
Ext file systems have a 5 % emergency reserve only root may write to. This is needed so the system can boot even if the root disk is full, because it needs to write (log files etc ...) during boot. 5% of ~20 GB is about 1 GB, leaving you with about 200+ MB.. So that actually fits. What doesn't fit are the numbers from du. If we disregard home, boot and media it adds up to about 10 GB. You should have 8 or 9 GB free. I'd boot from a live disk / USB stick and check that home, boot and media don't contain files that get hidden by he mounted drives and do a file system check on the root drive.

---

### Post by buzzcook on 2015-04-13
Thanks, Holger_Gehrke. I booted from Parted Magic and checked the file system - it went through successfully, see the output in the attachment.

How can I do the following as you suggested? 
"check that home, boot and media don't contain files that get hidden by the mounted drives"
And what would this tell me?

---

### Post by Holger_Gehrke on 2015-04-13
Just mount sda6 in a live system and take a look at the contents of those directories. If you mount a file system on a directory, the files in that directory -- if there any -- become inaccessible. They still take up space, though ...

---

### Post by buzzcook on 2015-04-13
Good, many thanks - seems to be fixed now.
There was a directory called truecrypt6 in media that was occupying 7.7 GB. I deleted it and the missing space has been recovered.
I recently noticed that Truecrypt was not dismounting properly on occasions so I presume it was due to this ...

---

