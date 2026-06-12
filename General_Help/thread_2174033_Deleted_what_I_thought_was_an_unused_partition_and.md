---
title: "Deleted what I thought was an unused partition and now I boot into GRUB menu"
date: 2013-09-12
forum: General Help
---

### Post by thesaxking on 2013-09-12
Hey guys

I am a bit of a n00b and deleted a partition that I believed to be an unused partition on my one and only drive... don't ask me why... I'm stupid...

Anyway, I'm running ubuntu 13.04 and all seemed to continue working fine until I restarted.  At this point it loads in the GRUB menu and selecting ubuntu fails.  It says:

ALERT! dev/mapper/ubuntu-root does not exist, dropping into shell.

I have no idea what to do now!

Any ideas?  I would ideally not like to lose anything on that drive...

Thanks in advance!

---

### Post by tgalati4 on 2013-09-12
If you have a CD/DVD or USB, boot from that.  Make sure you have a working, wired ethernet connection.  Install *testdisk* and hope that you can restore the partition table.  You want to be careful not to write or install anything to the disk drive.  Search testdisk for tutorials on how to use it.

---

### Post by ajgreeny on 2013-09-12
How did you delete the partition?

It looks as if you may have deleted your ubuntu root partition, ie the OS itself, so I presume you were not running ubuntu when you deleted it.

If you did this when running windows in a dual boot setup, bear in mind that windows can not see Linux partitions, so would have reported it as an "unknown partition", which may be why you were confused into thinking it was unused.

---

### Post by thesaxking on 2013-09-12
That's the bizarre thing, I _was_ running Ubuntu at the time... so a little confused if I've manage to delete the root partition!  I've not got a dual boot set up.

As for testdisk, I was going to try that but it doesn't seem to be installed on the livecd and I don't seem to be able to install it... although I was using a 12.10 livecd, but assume that's not a problem?

I have ordered a new hard disk anyway, so think I'll install that as root once it arrives, then I can access my previous disk from an installed version of ubuntu rather than a livecd.  I figure testdisk may be more successful that way and I can salvage my files.

If you think of anything else then do let me know!

Cheers

---

