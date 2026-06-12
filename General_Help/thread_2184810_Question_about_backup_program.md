---
title: "Question about backup program"
date: 2013-10-30
forum: General Help
---

### Post by sideburns on 2013-10-30
I use Fedora on my desktop, and keep it backed up with backintime to a flash drive that's been reformatted to ext4.  This backup program uses symlinks to represent files that haven't changed since the last backup, saving space and allowing you to have far more backups on the same drive before it needs to delete old ones.  Right now, I have about 25GB of data and about 9GB of free space on a 16GB drive, or at least, that's what the system says.

My sister is using Xubuntu and wants to start backing things up properly.  Checking, she has Ubuntu's default backup program installed.  What I'd like to know is, does it store things the same way as backintime does, or does it just make a new copy each time because how it works will be an important factor in deciding which program to use and how to configure it.

---

### Post by TheFu on 2013-10-30
a) backintime uses hardlinks, not symlinks - there is a subtle difference that is critical to the way that B-i-T works. Wikipedia has articles on each, if more understanding is desired.

b) using backintime under Ubuntu works the same. There were KDE and Gnome versions in the repos last time I checked.

c) there are more efficient backup methods than backintime for storage, but B-i-T is great and easy for end-user backups, but not-so-great for whole machine backups, IMHO.

I love B-i-T for individual user backups. Simple, to the point, and lets the end-users control it.

I don't know what the default backup tool is for that version of Ubuntu. The tool changes from time to time and different DE choices will impact as well.  I think they are using DejaDup now, which is based on Duplicity. Both are impressive backup tools.

---

### Post by sideburns on 2013-10-30
OK, I used the wrong term.  And, I'm sure that backintime is available for Ubuntu.  My sister wants to know if the default backup program will work, so I need to know enough about it to answer.

---

### Post by TheFu on 2013-10-31
> **sideburns said:**
> OK, I used the wrong term.  And, I'm sure that backintime is available for Ubuntu.  My sister wants to know if the default backup program will work, so I need to know enough about it to answer.

I looked around a little - couldn't determine the default program on xubuntu, but did find this: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)  It does confirm that DejaDup is the default on "Ubuntu Desktop"

Hope it helps.

---

### Post by philhughes on 2013-10-31
Any backup program is only as good as its restoration process. I lost faith with Deja Dup (which is the default backup program in Ubuntu) when during testing, the "Restore Missing Files" function didn't find any files to restore. The files were in the backup, as shown when I messed around briefly with the duplicity backend. Whatever program you use, test it!

---

### Post by TheFu on 2013-10-31
Ive never gotten duplicity to work well. Tried Duplicati over a year ago and it was .. S L O W.  

OTOH, Im not much of a GUI user - to me GUIs are just there to have more xterms open - so I can only recommend the 1 tool that has worked for me and my business the last 4 yrs - rdiff-backup.  The command is very much like rsync, which cmopletely rocks, just for different purposes, and based on librsync, so it is highly efficient. There is no GUI for it.  It doesnt encrypt as part of the backup process, but encrypted storage can be used, if that is important.  Ive found rdiff-backup to be more storage efficient than B-i-T, but different use patterns will probably have different results. It all depends on the files involved.

Definitely test whatever method you use, I agree with PH completely.

---

### Post by sideburns on 2013-11-16
Just to double-check the Restore facility of Back In Time, I removed a folder that I didn't need any longer and restored it.  It worked Just Fine.

---

### Post by TheFu on 2013-11-17
> **sideburns said:**
> Just to double-check the Restore facility of Back In Time, I removed a folder that I didn't need any longer and restored it.  It worked Just Fine.

Excellent test, however, if the folder had any non-standard files, basically it was just stuff under HOME, then that isn't enough of a restore test for me.  How does /etc get restored?  Are all the symlinks still symlinks and correct? Do they point to the relative files also in the backup or do they point to the /etc/ locations?  I would test this restore either on a system that can be reloaded or into a different test directory structure that will not harm a running system.  

OTOH, if all you want to backup are nominal ~/ files, then you are done.

---

