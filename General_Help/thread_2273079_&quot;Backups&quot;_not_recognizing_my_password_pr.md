---
title: "&quot;Backups&quot; not recognizing my password protected external storage backup"
date: 2015-04-10
forum: General Help
---

### Post by Mark_in_Hollywood on 2015-04-10
The Ubuntu default application (written by Michael Terry) called: 

Backups

would not recognize my password today. I have not changed the application's password. I have not changed my Ubuntu 14.04 LTS log-in password. (I tried both, just in case.) The password has been working until today for about a year or 18 months. Other than recent kernel updates and Ubuntu supplied updates of this week, I haven't added or removed any software or applications this week. I have saved files, surfed the 'net, read emails, and other regular operations.

The backed up files sit on an external SATA drive. 

```
Disk /dev/sdc: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1   781422767   390711383+  ee  GPT

```

The file manager (Nautilus) shows the files in the drive, here is one of those filenames:

duplicity-full.20150101T162738Z.vol4.difftar.gpg

The drives Properties shows:

Contents: 6,756 items, totalling 355.9 GB

if this problem is related to enough storage, I'm happy to delete these files and or re-format the SATA drive and start a fresh(er) "Backups".

Somebody gimme' a clue, please.

---

### Post by pmi2 on 2015-04-10
> **Mark_in_Hollywood said:**
> ...if this problem is related to enough storage, I'm happy to delete these files...Do you mean that you are unable to do more backups (add new files to the backup), or unable to restore files?  Restoring files would not require more storage, only backing up new files.

I believe that the archives produced by "Backups" are encrypted, so if you had a password when the first backup was created, then you need the same password to access it.  I don't think this is related to running out of storage space.

edit:

In other words, is "Backups" not accepting the "Encryption Password"?

---

### Post by Mark_in_Hollywood on 2015-04-10
> **pmi2 said:**
> do you mean that you are unable to do more backups (add new files to the backup), or unable to restore files?  Restoring files would not require more storage, only backing up new files.

I believe that the archives produced by "backups" are encrypted, so if you had a password when the first backup was created, then you need the same password to access it.  I don't think this is related to running out of storage space.

Edit:

In other words, is "backups" not accepting the "encryption password"?

**yes,** the "Backups" application does not accept or recognize the password that has worked, prior to today, for the last 12 to 18 months. I set the "Backups" app to use a password. The files on the external drive cannot be recovered ("restored") by merely moving it to another computer or such.The "User" must enter the password.

As always with security, passwords and such, the simplest solution is the best. I would prefer to re-format the external storage drive and start over, than attempt to modify the "Backups" app.

---

### Post by mcduck on 2015-04-10
I've had some issues with he Deja Dup ("Backups") asking for the password again and again, and strangely enough it seems to work fine as long as you type in the password and press enter to confirm (instead of typing in the password and clicking the OK button with the mouse to confirm). If nothing else that's worth a try...

edit: Also, these bug reports are worth noticing: [https://bugs.launchpad.net/deja-dup/+bug/1105630](https://bugs.launchpad.net/deja-dup/+bug/1105630) [https://bugs.launchpad.net/deja-dup/+bug/918489](https://bugs.launchpad.net/deja-dup/+bug/918489)

---

### Post by pmi2 on 2015-04-10
You should not have to reformat your drive, or anything drastic like that.  Simply deleting the backup archive, or moving it into a subdirectory, or changing the "Storage Location", should allow you to create a new backup using a different encryption password (?)

---

### Post by pmi2 on 2015-04-10
> **mcduck said:**
> I've had some issues with he Deja Dup...I have noticed some problems also, not sure if they are bugs or just quirks.  Most have to do with errors not actually indicating what the problem is (for example not being able to access the backup drive), or corrupting a directory when trying to restore a file from inside the file manager using the right-click "Restore Missing File..." option.  However, so far, not with the Encryption Password".

---

### Post by Mark_in_Hollywood on 2015-04-10
Dear mcduck. Sadly using the "Enter" key did not work for me.

PMI2. I deleted all the files on the external drive, using shift delete. On running "Backups" again, the app asked to pw protect the restore. I declined. It seems to be working for now and is backing up the /home


Thanks, Linux Community.

---

