---
title: "backup files - howto"
date: 2019-07-02
forum: General Help
---

### Post by jgw on 2019-07-02
I have had to reinstall and had everything, in theory, backed up on another drive.  I don't seem to be able to restore the files.  The files are .manifest and .gz files (duplicity).  I am at a loss.  I actually tried to restore with the backup program  that that errored out and said there were no files but there are a LOT of files.  They go back to january of this year.  I also gave the the program the information as to where they were.  It only recognized the first three months and couldn't even restore those without error.

Any thoughts on this one?

Thank you.................

---

### Post by CatKiller on 2019-07-02
The way duplicity works is that it takes a full backup at whatever time you've specified, and then takes incremental backups until the next full backup. You need a full backup and all the intervening incremental backups from prior to the date you're trying to restore to. Do you have those?

---

### Post by HermanAB on 2019-07-03
Hmm, this is why I prefer a simple rsync backup system.

Anyhoo, you should be able recover any old files form the last full backup using only the tar utility.  The difference backups may be more of a hassle, but it should be possible to go and manually dig in there too.

In essence, the backup set consist of a full backup which you can manually untar to another disk/directory, plus a string of small sets that you can untar over top of the first backup - whatever is different, will then add to or overwrite the original files.  

Read the tar man page.  This is not rocket science, just a pain in the neck to execute.

More information:
[https://linux.die.net/man/1/tar](https://linux.die.net/man/1/tar)
[http://duplicity.nongnu.org/duplicity.1.html](http://duplicity.nongnu.org/duplicity.1.html)
[http://duplicity.nongnu.org/new_format.html](http://duplicity.nongnu.org/new_format.html)

---

### Post by rbmorse on 2019-07-03
> **HermanAB said:**
> 
This is not rocket science, just a pain in the neck to execute.


I'm stealing this and putting it on a t-shirt

---

### Post by jgw on 2019-07-05
Thank you for the replies.

I thought I would make another run at backups.  It worked!  I have no idea why or how but I will now mark this as done.

It was a little strange.  It kept asking me for what to install.  I installed about 4 dates.  I probably did it wrong as I started with the most recent and worked back which made absolutely no sense.  I just didn't think it through.  That being the case I still found most of my stuff had been recovered so I am a reasonably happy camper.  Backups is a pretty strange program and there doesn't seem to be much documentation but it worked for me.  I will, however, take a look around to see what else there is.

Thanks again!

---

### Post by TheFu on 2019-07-05
Since computers had storage in the 1960s,  below is THE STANDARD monthly backup schedule:

```
S M T W T F S
- &#8211; - &#8211; - &#8211; - 
D D D D D D M
D D D D D D F
D D D D D D F
D D D D D D F
```

 [LIST]
[*]   D = Daily differential backup &#8211; changed data only, unless you can perform full backups within your backup window without impacting users
[*]    F = Full backups &#8211; this limits the number of daily backups to be restored if there is an issue that week to 6 or 7
[*]    M = Monthly &#8211; mark the first full backup of each month as the monthly and store it
[/LIST]

    If you have limited backup infrastructure, you may need to split the weekly/Full backups for different computers between multiple days like Friday, Saturday and Sunday. Since this complicates your overall solution, it should be avoided.

Old-school backup systems like duplicity, deja-dup, duplicati, dump, ufsdump and gnutar generally **SHOULD** follow this sort of schedule.  The actual implementation is left to the administrator.  The admin would choose when full backups happen.  The admin would choose when to save off the monthly "full" backup as the monthly to be retained.  The admin would choose how many monthly backups to retain and when the tapes/storage used should be returned to the daily/weekly "available" storage for use again.

To restore, the admin would pick the most recent "Full" backup, then apply the daily incremental backups in order to the date you want restored.

There are other sorts of backup tools which work differently.  rsync+hardlinks, back-in-time, rdiff-backup are the popular versions of those.

It shouldn't be necessary to say this, but until the restore process has been completely tested, there is no way to be certain that the backups are working or even useful in any way.  **TEST THE RESTORE!**

---

