---
title: "External HDD bad blocks"
date: 2016-04-01
forum: General Help
---

### Post by SamInside on 2016-04-01
So. My migration to Xubuntu was almost done, until I plugged in my external HDD (VERBATIM) and got problems, probably hardware though.

Table creation with GParted works fine (both msdos and gpt).
Formatting in ext4 with:
```
 sudo mkfs.ext4 -L label -E lazy_itable_init=0,lazy_journal_init=0 /dev/sdb1
``` gives the "Warning, had trouble writing out superblocks" message, which, searching the net, tells me that I've got hardware problems.

I'm currently running
```
sudo badblocks -vsw /dev/sdb
```
to check for bad blocks (will take forever :3).

My question is very simple: **then what?**

I mean, is there a way to correct / exclude those blocks, or do I just have to throw away this HDD and buy a new one?

(BTW S.M.A.R.T. doesn't seem to work on this drive)

---

### Post by sudodus on 2016-04-01
I use the method with e2fsck, which marks the bad blocks (and excludes them for the file system).

```
sudo e2fsck -cf /dev/sdxy
``` where x is the drive letter and y is the partition number.

See ```
man e2fsck
``` for details about the **-c** option.

Why is  S.M.A.R.T. not working? Is it a very old drive, or is something very wrong with the drive? You can live with a few bad blocks, but if this is a sign of a failing drive, you should get a new drive instead of wasting your time trying to fix this one.

---

### Post by SamInside on 2016-04-01
Just to be sure, does it make sense to run e2fsck, if my mkfs command itself didn't successfully create an ext4 file system in the first place, stopping when writing superblocks, as the message said?

(I'll investigate a bit more about the S.M.A.R.T. problem and come back with more details)

---

### Post by sudodus on 2016-04-01
If it was a warning message, it should be meaningful, but if it was an error message, no.

---

### Post by SamInside on 2016-04-01
You got it the other way around XD Anyway, it's written as a warning, so, well, I'll try your suggestion.

---

### Post by sudodus on 2016-04-01
Good luck :-)

And keep watching this drive - check regularly, if new blocks will turn bad.

---

### Post by SamInside on 2016-04-09
It was just broken. I bought another one, 3.0 instead of my old 2.0. Best thing.

---

