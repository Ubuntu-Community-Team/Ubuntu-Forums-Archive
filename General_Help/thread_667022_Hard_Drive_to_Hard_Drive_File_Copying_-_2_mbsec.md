---
title: "Hard Drive to Hard Drive File Copying - 2 mb/sec"
date: 2008-01-13
forum: General Help
---

### Post by optik678 on 2008-01-13
I need some help on my new Ubuntu 7.1 install.  I'm running the server edition on my box and am having some rediculously slow file transfer speeds between my IDE drives.  I thought it was, perhaps, the ufs (Used to be a FreeBSD box) file system messing it up so I copied my data between drives (slowly as well) and reformatted to the ext3 file system and rebooted.  It still copies at the slow speed and I'm baffled.  Unfortunately, I'm still a beginner with linux and just want to get this thing set up so I can set it behind my TV and forget about it :)

What tools can I use to track down why this is copying so slow?  I tried different variations of search terms in both google and on this board and didn't find anything that really applied to my situation.

Thanks alot for the help.

---

### Post by articpenguin on 2008-01-13
how big are the files?

---

### Post by optik678 on 2008-01-13
Anywhere from 3-5meg MP3s to 150meg TV Show Episodes to 700meg movies.

---

### Post by optik678 on 2008-01-14
Hmm, this is interesting : I was looking for file system tweaks and was following [This Guy's]("http://www.ubuntugeek.com/how-to-increase-ext3-and-reiserfs-filesystems-performance.html")instructions to increase ext3 performance.  When I tried to run the ```
tune2fs -o journal_data_writeback /dev/hda1
``` instruction on my swap partition, I got a bad superblock error.  This would probably explain my slow server, I would think, right?  If I use e2fsck to change to a backup superblock, do I lose the data on that partition?

---

### Post by articpenguin on 2008-01-14
i dont know if the superblock backup will corrupt the filesystem or not as i dont use ext3. Ext3 is good with those size files so it could be something else causing the problem.

---

### Post by optik678 on 2008-01-14
Anyone know what direction I should look to troubleshoot this?  If you could just point me in the right direction, I will do the reading/researching, I just don't know what terminology I need to use to get further in this search.

---

