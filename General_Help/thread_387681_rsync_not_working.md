---
title: "rsync not working"
date: 2007-03-18
forum: General Help
---

### Post by z08595 on 2007-03-18
I have two computers running Dapper.  Each computer is set up as a dual boot, and uses a FAT32 partition (/shared) to store my data.  I want to setup rsync for backups from the /shared directory on one to the other.

I set up a script like the one [here]("http://www.scrounge.org/linux/rsync.html"), and when I run it, the terminal looks like it's transferring files, and I show a large transfer rate in the system monitor.  When it finished, I tried to check my old computer for the transferred files.  The folders are all there, but there are no files in any of the folders (and they are not hidden either).

I also tried directly running ```
rsync -a /shared/ craig@192.168.2.40:/shared/
``` which didn't work either (craig being my username on both machines).

I also get errors that read something like: ```
rsync: failed to set times on "/shared/Documents/Fish": Operation not permitted (1)
``` for each folder in /shared, but I read that they don't mean much and can be suppressed by the -O option.

So, what am I missing?

---

### Post by hde on 2007-03-28
So only folders are transfered? Only the files are missing on the destination?

Do you get any other errors than the one posted?

Have you tried to transfer some files from your home directory to your other home directory (just to check that rsync works, and it's not a permission issue)

When you did

rsync -a /shared/ craig@192.168.2.40:/shared/

what was the error message?

---

### Post by aysiu on 2007-03-28
*rsync* doesn't work with FAT32. I found out the hard way.

It works perfectly with Ext3 and HFS+, though.

---

### Post by hde on 2007-03-28
Ok, tried rsync'ing some files to a fat partition, the files were transfered fine, however rsync complained that it could not chown the files which is not possible on a fat filesystem.

I once tried sync'ing to a fat partition, using unison, which could be an alternative to rsync ([http://www.cis.upenn.edu/~bcpierce/unison/]("http://www.cis.upenn.edu/~bcpierce/unison/")), but I wanted to keep permissions and timestamps on the files, and they changed to much when transfering to fat (the timestamps did).

Now I daily use unison on ext3 partitions.

Windows is also able to read ext2, that could also be an option [http://www.chrysocome.net/explore2fs]("http://www.chrysocome.net/explore2fs")

---

