---
title: "Backup software recommendations?"
date: 2008-02-04
forum: General Help
---

### Post by Guy Gizmo on 2008-02-04
I'm working on migrating my company's file servers from Windows XP to Ubuntu.  One of the pieces of software we used very regularly was SyncBack for doing regular daily backups on to a SMB-shared network drive.  So now I'm looking for some kind of similar piece of software for Ubuntu.

So far, I've found a lot of potential pieces of software for doing what we want, but I'm not sure which to choose.  We need this program to include several key features:
1. It *must* include a GUI for all the features we'll need, since people who aren't familar with Linux or the command line will occasionally need to use the program
2. It has to be able to synchronize two folders, one of which is on an SMB server
3. We need the synchronization to run automatically, once a day
4. It needs to be able to exclude certain files and folders from the synchronization by doing partial file name matches.  (Something like "*.jpg" or "specificFolderName")

Our plan B is to continue using SyncBack under Wine, since according to the Wine database all of its features work.  However, I'm skeptical to use a piece of Windows software under Wine for our important backups, and would much rather use something that runs natively in Ubuntu.

Does anyone have any suggestions?

---

### Post by Zill on 2008-02-04
Guy Gizmo:  I'm not sure what you mean by "It has to be able to synchronize two folders".  Do you want a clone of your folders on another drive?

If not, then SBackup is already on your PC (System, Administration, Simple Backup Config/Restore) and meets your other requirements.  However, this saves data as tar files to minimise size so isn't really "synchronizing" the folders.

---

### Post by Guy Gizmo on 2008-02-04
I think synchronizing two folders means to make them match, file for file.  In particular, though, if a file already exists in both the source and destination directory, then it copies over the source file if its modified date is later than the destination file.  So it only copies what needs to be copied.

In fact, this is what rsync does.  I looked around for a GUI frontend to rsync, and while one exists, it unfortunately isn't fully featured, and lacks a couple of the capabilities that we'd need.

I'll look into SBackup, but if it can only save the files as tar archives, that probably won't work for us.  The folders that are being copied are in the order of tens to hundreds of gigabytes in size, so making a tar archive of the whole thing is pretty infeasible.  We might want to access the individual files on the backup at some point, too.


edit: And I did look into SBackup, and it would've been great for what we needed, except that it would only save the backup as a giant archive.  Oh well.

---

### Post by Guy Gizmo on 2008-02-04
I just tried Unison as well, and it didn't work either.  It doesn't look like at has the sort of options we need, and furthermore it continuously failed to copy files in a test, and crashed on a couple of occasions.

So I think we're going to stick with using SyncBack under Wine.  It's rated as platinum in the Wine application database, so it ought to work just fine.

---

### Post by Zill on 2008-02-04
Guy Gizmo:  You may like to have a look at [flyback]("http://code.google.com/p/flyback/") and [TimeVault]("https://wiki.ubuntu.com/TimeVault").

I have not tried these and have no idea if they are any good or not but they may be the kind of apps you are looking for.

---

### Post by locolobo on 2008-02-05
Guy Gizmo, You might take a look "A new back-up solution if you want it" found now under
General Help in this forum by author> Mdpalow   ...  I think you will find it does all you want and MORE.......  Later

---

