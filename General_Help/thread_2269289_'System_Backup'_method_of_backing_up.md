---
title: "'System Backup' method of backing up"
date: 2015-03-14
forum: General Help
---

### Post by dtree46 on 2015-03-14
I have a 16gb pen drive that has an old backup made by the backup that comes with 14.04LTS.
How can the files 'duplicity****.difftar.gz' be opened and remain on the 16gb pen drive without actually restoring anything?
I just want to see what this backup contains.

dlw

---

### Post by buzzingrobot on 2015-03-14
> **dtree46 said:**
> I have a 16gb pen drive that has an old backup made by the backup that comes with 14.04LTS.
How can the files 'duplicity****.difftar.gz' be opened and remain on the 16gb pen drive without actually restoring anything?
I just want to see what this backup contains.



Simplest thing might be to point the Backup tool at the pen drive.

If there's room on the drive to expand the compressed files, then right-click a filename in the file manager and selecting 'Extract Here' should do precisely that. The extraction is non-destructive, i.e., it won't alter the archive.

If there's not room on the pen drive, copy the file(s) somewhere else.

If the archives were encrypted, you'll need the key.

Note that the "difftar" indicates the archive likely contains only the differences -- the things that changed in the targeted files -- between two runs of Backup.

---

### Post by dtree46 on 2015-03-14
Thank you for replying.
No luck.

dlw

---

### Post by pmi2 on 2015-03-14
> **dtree46 said:**
> No luck.... When you extract the folder using something other than "Restore" from the original backup program, are you getting an error that reads something like  this?> "Archive Type not Supported"...  If you are, there may not be any easy way to "look inside" the backup files without restoring them completely to some new location (by "new" meaning different from the original location).  The original Backup software may have produced archive files that only be opened from inside that program.

---

### Post by dtree46 on 2015-03-15
[ATTACH=CONFIG]260635[/ATTACH]

As you can see from theattached screen shot, I can open the .gz file with archiver to a .difftar.
Then open the .difftar with 'ark'. After that you see the error trying to open a file. A video in this case.
All this happens on the 16gb pen drive. Some progress anyway.

dlw

---

### Post by sandyd on 2015-03-15
That is a difftar which is a incremental backup

Easiest way to restore is by using the backup utility itself (deja-dup) or by using duplicity, which deja-dup is a frontend for.

You can restore using duplicity using [the guide here]("https://wiki.gnome.org/Apps/DejaDup/Help/Restore/WorstCase")

Deja-Dup automatically does the things in the link, which is why deja-dup is recommended over attempting to extract the backup using duplicity.

---

