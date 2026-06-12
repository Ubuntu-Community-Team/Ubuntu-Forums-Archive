---
title: "File list of every file on the HDD"
date: 2019-09-28
forum: General Help
---

### Post by UBUminJ on 2019-09-28
I have looked around but I didn't find a working solution.

I am using Ubuntu 19.04.

I want to list all files together with their location(path) and their size - nothing else.

find . lists all the files but can I add the filesize?
Is there another command which I should consider?

Thank you

---

### Post by Holger_Gehrke on 2019-09-28
The option '-printf "formatstring"' of find enables you to print out all kinds of information about the found files.
```
find / -printf '%p %s\n'
```
The '%p' in the format description is the complete path and name, '%s' is size in bytes. You might want to add the option '-xdev' to stop find from going into  other filesystems like /proc, /sys, /dev or mounted drives.

Holger

---

### Post by UBUminJ on 2019-09-28
Thank you Holger. It is solved.

---

### Post by TheFu on 2019-09-28
There is also the old **ls -lR** method, that was included in every CDROM with F/LOSS software from the 1990s.  If you find any Linux ISO/disc from that time, you'll always find a file in the ISO9660 root named LS-LR or something close to that.

Removing columns from text files is something any good text editor should accomplish trivially. vim does it.
Or you can use awk, sed, cut, perl, python, ruby, or any other minimally capable programming language.

Sometimes it is handy to sort by size, rather than location.  ls can do this without piping through sort.
**ls -lRS**

Anyway, there are many solutions possible.  Holger_Gehrke's is probably the best, based on the problem description.

---

### Post by oldos2er on 2019-09-29
> **UBUminJ said:**
> Thank you Holger. It is solved.

Please use Thread Tools at the top of the page to mark it so. Thanks.

---

