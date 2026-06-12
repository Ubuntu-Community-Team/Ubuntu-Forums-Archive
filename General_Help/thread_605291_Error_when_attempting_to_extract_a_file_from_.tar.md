---
title: "Error when attempting to extract a file from .tar"
date: 2007-11-06
forum: General Help
---

### Post by Nick Blinko on 2007-11-06
Awhile ago a friend of mine backed up my Soldier of Fortune game for linux incase I lost the cd. Well, recently I wanted to install it and play one of my favorite games but I couldn't find the cd anywhere so I loaded up the backup from my flashdrive.   When I attempt to extract the file I am confronted with this error:

tar: Pattern matching characters used in file names. Please,
tar: use --wildcards to enable pattern matching, or --no-wildcards to
tar: suppress this warning.
tar: Soldier of fortune linux/[[]games[]].Soldier.of.Fortune-Linux-[[]EN[]].iso: Not found in archive
tar: Error exit delayed from previous errors


Thanks in advance, I really appreciate it.

---

### Post by ohzopants on 2007-11-06
You could try the "--no-wildcards" switch as suggested, and see if that works.  I suspect the square brackets are causing the problem, those are usually used in regular expressions and really shouldn't be in a file name.

You could also try renaming the file to something without the square brackets and without spaces; I used to put spaces in my file names too, this led to so many headaches I finally stopped using them in file and directory names altogether.

---

### Post by Nick Blinko on 2007-11-06
Thanks alot, extracted and everything is fine.

---

