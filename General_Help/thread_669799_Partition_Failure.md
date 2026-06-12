---
title: "Partition Failure"
date: 2008-01-16
forum: General Help
---

### Post by jcfisher on 2008-01-16
I partitioned my hard drives according to the suggestion on the following site: [Cool Solutions: Install Linux Frequently, Without the Hassle]("http://www.novell.com/coolsolutions/feature/11802.html").  Essentially, it suggests that you make several partitions for your operating system(s), and one larger, communal partition for your data, connecting the two using symlinks.

This is a system which has worked well for about a year.  Yesterday, however, I turned on my computer and after telling GRUB to boot into Ubuntu, the loading progress bar disappeared and Ubuntu started telling me about I/O errors to ata2.  I put in the Gutsy CD, and received the same errors.  After about 20 minutes, the CD booted in spite of the errors.  I attempted to run fsck (which, I gather, is the Linux equivalent of Windows' chkdsk), but the partition, /dev/sdb2, doesn't show up!  The other hard drive, /dev/sda, seems to work fine, and the other partitions in /dev/sdb are visible, but not sdb2.

The whole point of the system that I mentioned earlier is that you can have some sort of crisis and still be able to wipe the partition without trouble -- like those watertight chambers in the hull of the Titanic.  Unfortunately, sdb2 is the partition where all of my data is, so you might say I've hit an iceberg of sorts.  At risk of stretching this analogy too far, can anyone help me get to a lifeboat?  That is, how can I save the data from my corrupted partition?

Thanks,

Jake

I've attached the boot log for the live CD, which should include the I/O error messages.

---

### Post by jcfisher on 2008-01-19
I solved my own problem, sort of.  I hope this "solution" can be of help to anyone else who has this problem.

So I figured out that fsck can scan partitions by UUID, and not just by /dev entries.  From the Ubuntu Live CD, I mounted the operating system's partition, and looked in /etc/fstab to find the UUID for the partition I hoped to repair.  I then ran 
```

$ sudo fsck -y UUID=[long string]
```
(the -p option returned an error).  After running the check overnight, my hard drive started beeping and clicking, and at that point I replaced it.

So - the solution is to find the UUID for the partition you want to repair and use that instead of /dev/sdb2 or whatever.  Just don't expect much from it.

---

