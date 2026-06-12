---
title: "Need help with Duplicity (Deja Dup) .. Ubuntu 18.04"
date: 2020-11-22
forum: General Help
---

### Post by frankdn01 on 2020-11-22
Hello and thanks for reading.  In my old installation of 18.04 I split my files between two partitions; most subdirectories (Desktop, Downloads, etc.) were in the partition housing my Home directory, but I kept Documents in a separate, larger, partition, with a symlink in Home that pointed to it.

Now, having installed 18.04 on another machine, *everything* is in one partition, i.e.: no symlink.  And Deja Dup tells me it can't restore my Documents files and asks if I have write permission there.  I do. (And Desktop, etc. did restore successfully.)

So the fact that 'Documents' now lives in the same partition as 'Home', and is no longer accessed through a symlink, breaks the restore operation?

How do I fix this?  I want my files back!  Waaah :-(

---

### Post by TheFu on 2020-11-23
I haven't a clue, but perhaps the single partition doesn't have enough space for the restore?
I don't use duplicity or deja dup.

---

### Post by HermanAB on 2020-11-23
Hmm, I learned my lesson with using complicated backup tools (Deja-dup was actually he last straw) and consequently I now only use super simple rsync scripts.  

The problem is when things go haywire, then I want to get at my files easily.  I don't want to be forced to build a new system exactly like the old system, just to get my files back.

Here is a description of what you would have to do to dig your files out of the backup set:
[https://itectec.com/ubuntu/ubuntu-how-to-restore-a-broken-deja-dup-backup-manually/](https://itectec.com/ubuntu/ubuntu-how-to-restore-a-broken-deja-dup-backup-manually/)

---

### Post by frankdn01 on 2020-11-25
Well it turned out all I needed to do was choose a directory to restore to, instead of taking the default "restore to original locations" option.

---

### Post by TheFu on 2020-11-25
> **frankdn01 said:**
> Well it turned out all I needed to do was choose a directory to restore to, instead of taking the default "restore to original locations" option.

Backups and restores need to be run with root privilege escalation to be able to read all the files regardless of permissions/owners and to be able to put all the files back with the correct permissions, owners, groups, ACLs and xattrs.  For 1-user data files, this isn't too important.  For system files or data files with multiple users involved, it is absolutely critical.  The file data is only 50% of a backup.  The other 50% is the owner, group, permissions, ACLs, and xattrs.

---

