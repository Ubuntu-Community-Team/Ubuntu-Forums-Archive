---
title: "Deja-Dup Restoring Files"
date: 2017-12-07
forum: General Help
---

### Post by speartip on 2017-12-07
Using Deja-Dup in Ubuntu 16.04.
If I delete a file, I can restore it by right clicking in the folder, "restore missing files" & let deja-dup do its thing.
However if I accidentally delete a file, then do a backup with deja-dup, then want to restore the file, it's not there anymore using the above method.
So my question. Is the deleted file forever lost once I do a subsequent backup, or is there any other way of retrieving it?

---

### Post by untrustytahr on 2017-12-07
> **speartip said:**
> Using Deja-Dup in Ubuntu 16.04.
 Is the deleted file forever lost once I do a subsequent backup, or is there any other way of retrieving it?

You can still recover the file but I do not think you can use deja-dup to do it and the file would have to have been backed up at sometime in the past.  Use duplicity with the time option to go back further and you would probably want to know the filename so you do not revert everything to the way it was at that time.


If you have an rough idea of the filename...

```
duplicity list-current-files -t 1D <Backup Location> | grep -i <filename>
```

Once you have the name you can use

```
duplicity restore --file-to-restore <relative path to file from above> -t 1D <Backup Location> <Destination Location>
```

the -t 1D essentially is saying "the way the file was 1 day ago.

---

### Post by speartip on 2017-12-07
Thanks for your reply untrustytahr.
it seems like a lot of hard work, for what should be quite a simple restore procedure. I like the idea of deja-dup, but it doesn't seem to have the functionality of Areca. Think I'll stick with that as my default backup program.

---

### Post by rbmorse on 2017-12-07
Back in Time, in repository, will do what you want.  It saves multiple instances of the dataset sorted by date and time.  If you delete a file and there's a subsequent backup, you can still get a copy of the file from a backup set that was created prior to the deletion. The program has a user configurable "smart retention" feature that automagically trims backup sets as time passes. 

The downside of this is, of course, significant space requirements.  How significant depends upon your backup store.  I bought a 3 TB WD red series drive when it was on sale for $80 and use thatso for my desktop space is not an issue. If the system you're looking to backup is a lappie of some sort then you will have hard decisions to make.

---

### Post by untrustytahr on 2017-12-07
> **speartip said:**
> Thanks for your reply untrustytahr.
it seems like a lot of hard work, for what should be quite a simple restore procedure. I like the idea of deja-dup, but it doesn't seem to have the functionality of Areca. Think I'll stick with that as my default backup program.

To each his own...  I do not use the deja-dup gui much.  Poking around a little more it seems like you can revert the parent folder that contained the 'missing' file to a particular date.  That would restore the file but also all other changes since that last backup.  You could probably cheat if you new the exact filename by doing a touch and right clicking and reverting to a previous version.

I'm not familiar with areca but if it meets your requirements great.

---

### Post by speartip on 2017-12-08
Hi rbmorse...
I checked out backintime, but it faults out when using encryption. Also it has no dummy run facility to show exactly what is being saved. The reason I use Areca is that Linux Format magazine recommended it as the most full featured for Linux, & from what I see they are probably right.
 I just would prefer to use something more integrated to the system, hence the deja-dup question.

---

### Post by mastablasta on 2017-12-08
another one with many options is Duplicati.

Deja-dup is no more integrated that Areca. it is just an app.

if you are "backing up" on the same disk then you could explore BTRFS file system and use it's snapshots. they can restore the whole thing back to where it was. it is way more advanced than restore points in windows.
yet another option in the file system department (but might need more processing power) is ZFS4Linux.

---

