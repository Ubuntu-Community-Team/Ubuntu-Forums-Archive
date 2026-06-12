---
title: "External Hard Disk is not empty but files are not being displayed"
date: 2017-08-18
forum: General Help
---

### Post by msian on 2017-08-18
Hi
I've Ubuntu 17.04 running on my desktop. 
Recently I bought an external 2TB Seagate Hard Disk, which I formatted as ext4.
I've been using it for a couple of weeks without problem.
I've done nothing on my system but keeping it updated (daily check). 
And now, suddenly, it looks like empty. 
No files are displayed by **ls** or in nautilus.

At the mount point, **ls** returns: "Mensaje erróneo" (=Wrong message)

No active lines in **/etc/fstab** refer to this device / mount point

The output of **sudo fdisk -l** is:

[INDENT]Disk /dev/sda: 1,8 TiB, 2000398933504 bytes, 3907029167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: dos
Disk identifier: 0xbcf11af0

Disposit.  Inicio Start      Final   Sectores  Size Id Tipo
/dev/sda1          2048 3907024895 3907022848  1,8T 83 Linux
[/INDENT]

Any suggestion?

---

### Post by TheFu on 2017-08-18
Take it back to the store and get a new drive.  Might want to look through some HDD failure rates.  2TB Seagate drives were some of the worst made in the last 15 yrs.  "backblaze drive statistics"

---

### Post by msian on 2017-08-19
It is 20 days since I bougth it. No changes allowed by this time in Mediamarkt. 
And I want to recover the data.

More details: fsck detected some problems on several i-nodes and directories.
I answered yes to all questions (all them seemed reasonable to me, and saw no better choice).
At the end, nothing seems to have changed.
No files are shown.

---

### Post by #&amp;thj^% on 2017-08-19
> **msian said:**
> 
And I want to recover the data.
At the end, nothing seems to have changed.
No files are shown.

Sorry to hear this, but give this a look: [https://www.cgsecurity.org/](https://www.cgsecurity.org/)
I have had a lot of success with the two tools mentioned in the link.;)
Good Luck

---

### Post by efflandt on 2017-08-19
Seagate should have a warranty on it unless gray market. You may need to run tests with their SeaTools (which should be available as bootable iso) to prove if it is bad.

I had a Maxtor drive long ago that came in a Seagate box before I thought they merged, and that drive failed within a month of new. The Seagate drive on my current PC from 2010 began failing in 3 years. Not that I have not had Western Digital drives rarely file too in the many years I have had computers. But one warranty replacement WD drive in a 333 MHz Celeron PC with 158 MB RAM has been running Linux (SuSE 8.2) almost non-stop 24/7 since 2003 as an experiment. Originally I used that to learn apache name based virtual web hosting (with noip.com public names), sendmail, and postfix.

---

### Post by msian on 2017-08-19
Problem solved.
"**sudo ls lost+found**" showed missing files and directories, but with numerical names.
Thanks

---

### Post by #&amp;thj^% on 2017-08-19
> **msian said:**
> Problem solved.
"**sudo ls lost+found**" showed missing files and directories, but with numerical names.
Thanks

Good to hear! :)

This is just a bit of information only (Mainly for ext/2 thru ext/4)<<< not meant to be followed as you seem to be happy with your results you have now!	

If you run** fsck**, the filesystem check and repair command, it might find data fragments that are not referenced anywhere in the filesystem. In particular, fsck might find data that looks like a complete file but doesn't have a name on the system &#8212; an inode with no corresponding file name. This data is still using up space, but it isn't accessible by any normal means.

If you tell** fsck **to repair the filesystem, it will turn these almost-deleted files back into files. The thing is, the file had a name and location once, but that information is no longer available. So fsck deposits the file in a specific directory, called lost+found (after lost and found property).

Files that appear in** lost+found** are typically files that were already unlinked (i.e. their name had been erased) but still opened by some process (so the data wasn't erased yet) when the system halted suddenly (kernel panic or power failure). If that's all that happened, these files were slated for deletion anyway, you don't need to care about them.

Files can also appear in lost+found because the filesystem was in an inconsistent state due to a software or hardware bug. If that's the case, it's a way for you to find files that were lost but that the system repair managed to salvage. The files may or may not contain useful data, and even if they do they may be incomplete or out of date; it all depends how bad the filesystem damage was.

On many filesystems, the lost+found directory is a bit special because it preallocates a bit of space for fsck to deposit files there. (The space isn't for the file data, which fsck leaves in place; it's for the directory entries which fsck has to make up.) If you accidentally delete lost+found, don't re-create it with mkdir, use mklost+found if available.

---

