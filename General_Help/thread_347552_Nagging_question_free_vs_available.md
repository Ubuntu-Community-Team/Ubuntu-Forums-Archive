---
title: "Nagging question: free vs available"
date: 2007-01-27
forum: General Help
---

### Post by petehall on 2007-01-27
A question that has bugged me for a while - when I open up the System Monitor and go to the File Systems tab, the difference between the "Free" and "Available" columns is significant - about 5% of the entire drive.

What is the difference between these two values? Why is some of my hard drive space free, yet unavailable? I can't find any answers to this question anywhere, and the associated help file seems to be out of date.

---

### Post by mrgrapefruit on 2007-01-27
this is a random guess, but i'd wager some of the difference is allocated virtual memory. other than than you might need to defrag. without more details thats about all i can say!

---

### Post by r4ik on 2007-01-27
-

---

### Post by Insomniac20k on 2007-01-27
Do you dual boot?

---

### Post by petehall on 2007-01-30
> **Insomniac20k said:**
> Do you dual boot?

Yes, I have Windows XP on /dev/hda1, but surely that should have no effect upon the amount of available space on /dev/hda2 and /dev/hdb1.

---

### Post by flyingbrass on 2007-01-30
By default 5% is reserved.  From the mkfs.ext3 manpage:
> **-m** _reserved-blocks-percentage_
              Specify the percentage of the filesystem blocks  reserved  for  the  super-user. This avoids fragmentation, and allows root-owned daemons, such as syslogd( 8 ), to continue to function correctly after non-privileged processes are prevented from writing to the filesystem.  The default percentage is 5%.

---

### Post by petehall on 2007-01-31
flyingbrass gets the points. Thank you.

My research had led me to the conclusion that it was some sort of "filesystem overhead", but this makes perfect sense.

Since one of my drives is used solely for media files, I might use tune2fs to lower this to 1% and reclaim a few gigabytes.

---

### Post by glotz on 2007-01-31
I remember wondering this sometime myself. The help function was useless as ever...

"if you want to paiwhjfpwabpabg, press the paiwhjfpwabpabg button"

---

### Post by petehall on 2007-02-03
> **glotz said:**
> I remember wondering this sometime myself. The help function was useless as ever...

"if you want to paiwhjfpwabpabg, press the paiwhjfpwabpabg button"

Oh, it was worse than that. The Help function seemed to be describing some old version of System Monitor that didn't even have these columns.

---

