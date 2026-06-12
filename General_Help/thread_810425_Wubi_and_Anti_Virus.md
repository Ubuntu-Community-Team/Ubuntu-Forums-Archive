---
title: "Wubi and Anti Virus"
date: 2008-05-28
forum: General Help
---

### Post by bob-linux-user on 2008-05-28
Greetings.
These are my experiences using Wubi. I hope they are useful to others.
-I used the ordinary setup/Live CD from Ubuntu (Hardy)
-Ran Wubi from within Win XP to create a dual booting PC. Very pleased at this stage as I find all the mucking about partitioning a bit tedious.
-(after some weeks) installed Avast Anti Virus for Linux.It found a virus on the Ubuntu part of the Hard Disk (almost certainly contracted using Windows). It could not clean it though.
-Installed Avast Anti Virus for Windows on the same PC(previously ran AVG). It (unsurprisingly) found the same virus. It could clean it off but only by deleting the .disk file that Ubuntu sits on in Windows.
-Result is I have no Ubuntu.
-Will use partitioning next time.

Regards
Bob

---

### Post by ago on 2008-05-28
In Linux you can download viruses, they are just not executable.

It would have been interesting to know which file was marked as suspect by the a/v.

There have also been reports of wubi/initrd being marked as viruses which turned out to be false positives on the heuristic programs

---

### Post by abn91c on 2008-05-28
before you reinstall update your Av signatures in windows, run a full scan then defrag the HDD

---

### Post by bob-linux-user on 2008-05-28
Thanks Ago and abn91c. I will certainly do a thorough scan and clean up before reinstalling. I would have been interested to find which file was marked as having a virus but the Windows AV scanner just said it was the *.disk ( I can't remember the prefix) file which had the virus. This was of no use really as it is the whole of Ubuntu as represented in Windows. The file was about 15 gigabytes. I will repartition and install the usual way so this time have a "proper" dual boot PC.

---

