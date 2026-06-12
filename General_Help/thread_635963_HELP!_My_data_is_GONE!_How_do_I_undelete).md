---
title: "HELP! My data is GONE! How do I undelete)"
date: 2007-12-09
forum: General Help
---

### Post by slacker9876 on 2007-12-09
OK here is the scoop, I am a 15 year veteran of IT and I have lost my data. I was forced to rebuild my primary server as a Windows 2003 domain controller, so I formatted my disk believing it was backed up on my external drive, which I did just a week ago. After I rebuilt the server I installed Linux, connected the external disk, and all that was on it was lost+found. :-({|=

Apparently at some point I opted to delete the files from the external disk, kick me later, I don't even know why I did it. However, I know that I must have used rm * /media/disk/* This disk has not been formatted, repartitioned or overwritten. The volume creation date is consistent with my last backup, when I made a fresh volume.

Is there an undelete command that may be used for the ext3 filesystem? I am also willing to purchase commercial software. I just want this data back using a known working method. This was all my MP3's, documents, spreadsheets and ISO files for every CD and DVD I have ever purchased.

Please help!

---

### Post by p_quarles on 2007-12-09
I'm sure you're kicking yourself plenty, so I'll just say "ouch."

The package "testdisk" (in the repos) can be used to recover data. I've never had to use it myself, so can't help you there, but thought I'd point you in the direction of the standard tool for this.

---

### Post by slacker9876 on 2008-03-16
I know this is an old thread but I wanted to follow-up with the result. I purchased the Linux recovery utility from [http://www.diskdoctors.com/](http://www.diskdoctors.com/) and recovered most of my data. It was $100USD but it also saved me what would have been hundreds of hours in re ripping MP3 and video as well as all the ISO's of different distros I have pulled on DVD.

Just to share in case someone else messes up.

Also I should note that data recovery from ext3 file systems is a PITA, so if you don't have to I would stick with ext2 which this utility all but guarantees recovery. I am also running a backup to an external disk now :)

---

### Post by justleen on 2008-03-16
i had a lot of success with testdisk... There is also [autopsy,]("http://www.sleuthkit.org/autopsy/") this is very elaborate tool , but you can get every bit back (think the CIA orso developed it).

[Spinrite]("http://www.grc.com/spinrite.htm") is very good as well. Non free, but always available on the usual spots (but why go illegal if there GNU/GPL softare i say)

---

