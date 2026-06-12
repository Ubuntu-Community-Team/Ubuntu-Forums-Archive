---
title: "How do I know where all my diskspace went?"
date: 2006-10-21
forum: General Help
---

### Post by jsmidt on 2006-10-21
The other day I had 30GB on my hard drive left.  Now I have three.  I have not downloaded or uploaded or whatever than much stuff in the last few days.

How can I tell which directories contain the most disk usage so I can diagnose the problem?

---

### Post by lloyd_b on 2006-10-21
> How can I tell which directories contain the most disk usage so I can diagnose the problem?

In a terminal window:

[B]cd /
sudo du > diskused.txt[/B]

This will create a file ("diskused.txt") in the root directory, with a listing of all directories on the machine, and the amount of space used by the files in each of them.

This is run with a "sudo" because there are many directories that aren't accessible without it.

Be warned - it may take several minutes to run this command (and the hard disk light will be blinking like crazy the entire time).  There are a LOT of subdirectories on a typical Linux system, so it takes a long time to scan them all.

Lloyd B.

---

### Post by jsmidt on 2006-10-21
Thansk a lot.  It worked perfectly. :) I found the culprit: apt-mirror.  I installed it thinking it was something different then it was.  Come to find out it turned my computer into an Ubuntu mirror and filled my entire harddrive,  I would never have found this out without your help.  It resides in /var/spool!

---

