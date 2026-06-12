---
title: "Backup Question using Simple Backup Config"
date: 2008-07-08
forum: General Help
---

### Post by MeanStreak on 2008-07-08
Hi,

I'm using Simple Backup Config (available via the System file menu) to do a custom backup every week or so to an external storage device. 

After the latest backup I ran this evening, I decided to extract the files.tgz to confirm the contents was accessible and complete. Good thing I checked because gzip is failing with an irrecoverable error as follows:
```

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
```

Could someone please advise? 

Do I need to use Simple Backup Restore to restore my files? Is there any way I can verify the backup is successful without restoring the entire back up?

---

### Post by danwood76 on 2008-07-08
Simple backup does incremental backups, this saves on disk space and so on.
Its easier to restore with simple backup.
Im assuming it does something funny with the tars and thats why you cant open them.

You can do the tar-ing manually which will give you complete tar files.

---

### Post by MeanStreak on 2008-07-08
Thanks, yes, I suspect you're right - it must be doing something funny to the tar files. 

I just wish there was a way to confirm the integrity of the backup data before that fateful day when a restore is required. By then it will be too late.

---

### Post by danwood76 on 2008-07-08
You can use the manual tar method which I use, you can put it in the form of a bash script so you can just click an Icon and it does it.

Have a look through the sbackup options, you might be able to turn the incremental backup off so it stores a complete one each time.

---

