---
title: "synchronising folders"
date: 2008-05-28
forum: General Help
---

### Post by daz4126 on 2008-05-28
I've just made an exact copy of my documents folder onto an external drive.

Rather than keep dragging and dropping every now and then, can I use Rsync to synchronise these two folders so the copy on my external hdd will be an exact up to date copy of the folder in my home directory?

If this is possible, could somebody provide some instructions?

cheers,

DAZ

---

### Post by kpkeerthi on 2008-05-28
```
rsync -a --delete ~/Documents /media/Backup/Documents
```

-a => Archive mode. This is equivalent to -rlptgoD. It is a quick way of saying you want recursion and want to preserve everything (including permissions).

--delete  => delete files that don't exist on the sending side

[Man Page]("http://optics.ph.unimelb.edu.au/help/rsync/rsync.html")

---

### Post by barnex on 2008-05-28
rsync is indeed the best way to do this. Check out the options, I use:

```

rsync --archive --fuzzy --delete-after --backup --backup-dir=/media/Backup/Documents.previous --progress --stats --human-readable --max-delete=1000 ~/Documents /media/Backup/Documents

```

This will keep a 'previous' version were accidentally deleted files can be recovered, and prevents disasters by not allowing more then 1000 backed up files to be deleted.

The possibilities of rsync are endless, you can definitely write a script that suits exactly your needs.

---

### Post by daz4126 on 2008-05-28
Thanks for the replies guys, I will give the solution a go.

You both recommended using --archive, but barnex you added --fuzzy, what does that do?

Also what is the difference between  --delete and --delete-after?

Sorry for asking about trivial things - I just want to learn how this thing works!

thanks again,

DAZ

---

### Post by barnex on 2008-05-29
> **daz4126 said:**
> 
but barnex you added --fuzzy, what does that do?
Also what is the difference between  --delete and --delete-after?


--fuzzy is not really necessary, but it can speed up the transfer (e.g. over a network): when you changed a filename, rsync will normally delete the file in the backup and copy a new file with the new name to your backup. with --fuzzy, rsync will first look for files with similar names and see if it can just rename the file to obtain the same result (possibly modifying the content a bit too). It works well for names with a typical version name, like file-1.0.3.

--delete-after will not delete files until after the entire backup is complete. this is useful when the backup gets interrupted for some reason.

good luck with it.
greets.

---

### Post by daz4126 on 2008-05-29
Thanks for that explanation barnex - very useful. I've just got a couple of things I'd like to check before I go ahead and set up some synchronising:

* Once I have issued that command does rsynce just automatically monitor and update the folders when I change one of them, or do I have to use that command after every time I update the folders?

* What if I want to stop synchronising the files? Is there a command to do this?

Rsync certainly sounds like an excellent and very powerful tool. Is there a gui for doing this sort of stuff?

cheers,

DAZ

---

### Post by chrisccoulson on 2008-05-29
Also note you can do a dry run with rsync, which will tell you what files are going to be copied and deleted without actually making changes (to make sure it isn't going to do anything too bad) by specifying the '-n' option

---

### Post by barnex on 2008-05-29
> **daz4126 said:**
> 
* Once I have issued that command does rsynce just automatically monitor and update the folders when I change one of them, or do I have to use that command after every time I update the folders?

No, you have to run that command every time you want to backup. You can of course make a script or an alias to save yourself some typing. If you want automatic backups, you can use 'cron'

> **daz4126 said:**
> 
* What if I want to stop synchronising the files? Is there a command to do this?

Just hit 'Ctrl-C' to do this. The next time you run the backup, the rest of the files will be transferred so you won't have lost any time.

> **daz4126 said:**
> 
Rsync certainly sounds like an excellent and very powerful tool. Is there a gui for doing this sort of stuff?

I have no experience with these, but people at my university are using backuppc and seem to be quite happy with it. Not sure if this is what your are looking for however.

cheers,
barnex.

---

### Post by daz4126 on 2008-05-29
Thanks for the info - I've found two programs:
flyback and timevault that seem to be front ends for rsynce. I'm testing them out.

DAZ

---

