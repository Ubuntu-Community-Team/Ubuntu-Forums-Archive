---
title: "Re: disk full error"
date: 2012-11-26
forum: General Help
---

### Post by concord on 2012-11-26
I'm having the same issue.

Lenovo E430
500 GB Sata HDD
/dev/sda1 swap
/dev/sda2 ext4 (452 Gig) partition

Last week error messages showed out of disk space.  Unmounted /dev/sda2 and e2fsck reported no problems.  Xorg wouldn't launch because there wasn't any disk space.  Deleted a few small problems and Xorg w/desktop came up but disk still reported extremely low on space.  Also noticed that SD Media Card was no longer mounting automatically at /media/Backup where it had been (possibly unrelated).

After rebooting into rescue mode and fiddle farting around I rebooted and the /home directory suddenly stopped reporting 430+ Gig and correctly reported 3.1 Gig of files.

Machine worked fine for 3 days without a reboot and then today it happened again. - Showed 430+ Gig in the /home directory and same in the ~/ directory.  Is this a filesystem issue with large partitions?  Is it an ext4 problem?  What can I give you to help solve this?

Thanks in advance:confused:

---

### Post by wildmanne39 on 2012-11-26
*Thread moved to **General Help**.*

---

### Post by philinux on 2012-11-26
See this.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by concord on 2012-11-26
Did all that.  That's the problem ... it makes no sense

[http://www.pastebin.com/4u48wXuC](http://www.pastebin.com/4u48wXuC)

/media/Backup is an SD Card which I use to store /home/joyce using rsync nightly.  It shows 4.1G (which is actually correct) yet /dev/sda2 (/) shows 432G Used and 100% full (which is also incorrect because the partition size is 455G.

When I do a `du -chs /home/joyce` it shows that directory with a size of 432G, so it definitely thinks that home directory for user "joyce" is using 432G of space - it's not.

This happened before and then mysteriously after rebooting, running fsck.ext4, e2fsck, booting in rescue and remounting (`mount -o remount, rw /`) it cleared up.  What other information can I provide that will help?

Again, thanks.

---

### Post by philinux on 2012-11-26
Have you checked roots / trash?

---

### Post by concord on 2012-11-26
I found the problem although I don't immediately know how to fix it.  It was the .xsession-errors.old file @ 425G (wow)

[http://www.pastebin.com/kQ7WS4g9](http://www.pastebin.com/kQ7WS4g9)

I've deleted the file but will check back to see what new errors occur.

Thanks for the assist.

---

