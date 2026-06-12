---
title: "Point in time recovery in Ubuntu 11.10"
date: 2013-08-29
forum: General Help
---

### Post by Paul_Stinerck on 2013-08-29
I cannot quite understand what Ubuntu is doing with its backup and recovery tool. I have a box with Ubuntu 11.10 and I have happily been creating an incremental backup for some months now. The moment has come where I have deleted a few hundred important files and wish to go back to a point in time before the deletion. 

I am using the default backup / restore facility that comes with Ubuntu 11.10 and is launched from SYSTEM SETTINGS - BACKUP

The interface of the restore tool is quite simple. It populates the backup location and then finds the various backup dates. Now in my case I made a the following backups
22/02/2013 FULL
26/02/2013 INCREMENTAL
12/03/2013 INCREMENTAL
27/03/2013 INCREMENTAL
20/04/2013 INCREMENTAL
01/05/2013 INCREMENTAL
After which I was a bit lax in making the backups. 

On or around 14, 15, 16/07/2013 I lost a few hundred files but did not notice til yesterday 28/08/2013 as I had been on holiday. Today using the restore facility SYSTEM SETTING - BACKUP - RESTORE. From the backup location it found all of the backups above and asked me where it wanted to restore from. It asks "Restore from When?" in the dialog. I was thinking that in choosing 01/05/2013 my most recent incremental backup it would restore files that exisited on or before 01/05/2013, thus taking me back to a point in time prior to my file loss.

But it does not do this. In the file location where I restored to (not the original location, but a staging area to receive the restored files) there are files with dates after 01/05/2013. 

Now, reality check. I would have thought that in choosing "Restore from When?"=01/05/2013, I am asking Ubuntu to restore to a staging area the file system back to its state on 01/05/2013. But there are files restored with the date 15/07/2013. Now how can a backup from 01/05/2013 have within it files to restore from 15/07/2013. My interpretation is that the "Restore from When?" means restore files FROM 15/05/2013 ONWARDS. I don't know. Certainly we haven got a Point In Time Recovery back to 01/05/2013, because there are files from after this.

I have tried to find reasons for this
1. There is some kind of auto background backup going on all the time, even though I did not choose this and choose to disable this. This is pretty unlikely because in the most recent manifest and giftar files from the backup area are from 01/05/2013. There are no later backup files
2. None the less, even though there are no later files comprising the backup than 01/05/2013, the folder in which they are kept has a most recent change of 05:05 on 19/07/2013. I recall that I did an abortive backup that day that I killed. It makes me think that although no visible files were produced there are some files somewhere that interpret my instruction to restore to 01/05/2013 to include the state from this most recent abortive backup. But where is it getting its restore data from if the most recent manifest and giftar files are stamped 01/05/2013

OK, all this is conjecture. What I need please is the following
¿? 1º - how can I use what I have got (basically giftar and manifest files from a FULL & INCREMENTAL set in 6 phases) to get back to a restore from 01/05/2013?
¿? 2º - can the giftar and manifests be mined to bring out certain named files? How would I do this?

It would help me a lot if persons could answer these final two questions. It would also interest me immensly if anyone could explain to me how my restore was able to bring back files from after my most recent backup, but the priority is to get back to a point in time of 01/05/2013

Thanks for your attention.

---

### Post by JKyleOKC on 2013-08-29
I have no idea why you would have more recent files restored, although it's possible that some of them were created by that aborted backup and are in the backup directory although not included in the manifest.

However your post indicates an incomplete understanding of how incremental backups are supposed to work. They back up **only** those files that have changed since the last full backup. That means that if you only changed one file between 22/2 and 26/2, the incremental made on 26/2 would contain only that **one** changed file.

It also means that to restore the entire system, you have to first restore the most recent full backup prior to the date of interest, and then restore in sequence each of the incrementals from that full backup to but not past the date of interest! This can be extremely tedious if you have a number of files that are modified daily, since each day's version will be restored and then overwritten a few minutes later. That's why most folk recommend doing a full once a week or so and using incrementals only to capture the daily changes.

Not all backup programs do things this way, but this is the accepted industry standard terminology. At least one backup program -- backuppc -- automatically handles things when you restore from one of its incrementals. Unfortunately I don't know exactly how the one you are using does it.

Hopefully someone else will be able to give you a more detailed answer about the too-recent files...

---

### Post by Paul_Stinerck on 2013-08-30
Thanks JKyle for the reply
> However your post indicates an incomplete understanding of how incremental backups are supposed to work

I do indeed, I am an Oracle Administrator. I did not explain myself in the post properly. I used the GUI functuionality of the Ubuntu 11.10 backup / recovery default tool, and in choosing the date I assumed the tool took care of first the full restore and then the incremental up to a certain date. I was surprised to find files after that date. As I am using an obsolete version of Ubuntu maybe I should have explained myself better. I will apply your advice though, and explicitly bring back the FULL and then apply the INCREMENTS just in case the tool is not as clever as it seems.

Thanks again

---

### Post by JKyleOKC on 2013-08-30
Sorry, I didn't mean to sound patronizing; in this medium we can only go by the content of a posting.

I suspect that the tool you're using isn't really that clever, and that the later aborted backup created some files that had not been added to the manifest before you cancelled it. All backup strategies must compromise between speed and safety, and speed may have won in this area...

---

### Post by Paul_Stinerck on 2013-08-30
> I suspect that the tool you're using isn't really that clever

No Jim, it was *me* who was not really being very clever. Instead of having my documents on backup, I had a softlink to documents in the area that I was backing up, so each time I did a restore it brought back the softlink, which then pointed to the area where the documents are. Hence the fact I had documents dating from after the backup date, which kind of confused me. I had arranged the presentation layer of the gnome so that my documents looked as if they were in a certain place, and then had forgotten I'd done that. So I was simply backing up the pointer, and each time I restored it, it always pointed at whatever files were in the real location.

I did not consider your reply patronizing. I had merely written the thing in a rush and did not express myself well.

Thanks again for the advice

---

### Post by Paul_Stinerck on 2013-08-30
This is now solved. Does anyone know how you add the [SOLVED] tag to a post? I have looked everywhere for instructions.

Reason for solution - I have now found a backup at the file system level which has everything I need to recover.

---

### Post by Frogs Hair on 2013-08-30
In your first post,  use  Edit Post > Go Advanced and change the prefix to solved.

---

### Post by JKyleOKC on 2013-08-30
Or, even easier, follow the link in my sig below (the tool seems to have been fixed, at last)...

---

