---
title: "Files Vanished from External USB Drive"
date: 2007-05-19
forum: General Help
---

### Post by T700 on 2007-05-19
Kubuntu Fiesty Fawn 7.04 with all current patches.  Seagate external USB drive.  ext3 file system.  127G with 95G free.

Went to bed last night and all files were visible and readable.  This morning, when opening the drive in Konquer or on the command line, only one directory with a few files is visible.  Strangely, if I check the properties of the drive, exactly the same amount of space is free, leading me to think that the data is still there.

Not sure what other information will be useful to troubleshoot this.  

Paul

---

### Post by Cene on 2007-05-19
Maybe the files are hidden?

Does *du -h /path/to/media* or *ls /path/to/media* recognize the files?

---

### Post by T700 on 2007-05-19
That was exactly it.  The files had been delete and were in the hidden directory .Trash-1000.  In my panic, I didn't think of the most basic thing.  I've got them restoring now.

Next, the big question:  What did I do that caused this?  Ah well, life's a mystery and this is just another adventure!  :-)

Thanks for your help!!

Paul

---

