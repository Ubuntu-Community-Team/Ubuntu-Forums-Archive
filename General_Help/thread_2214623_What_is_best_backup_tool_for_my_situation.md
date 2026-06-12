---
title: "What is best backup tool for my situation?"
date: 2014-04-02
forum: General Help
---

### Post by sim085 on 2014-04-02
Hello, I have done some searching on back up solutions and I found plenty of tools. However I do not know which is the best one for my particular situation. I have a machine with three drives. Two of these drives are software raided. I would like to use the other drive to store files from the raided drives as a backup just in case something happens to these two. I have Ubuntu Server 12.3 installed. 

In other words all I would like is a tool that will automatically move files from one drive to another only if there are changes to these drives. The tool I am looking for ideally would allow me to add new directories to be backed up.

---

### Post by vanadium on 2014-04-02
rsync automatically run at regular intervals using a cron job?

---

### Post by Lars Noodén on 2014-04-02
Yes, rsync would do that.  If you are just watching a few directories, then incron can be used instead of cron.  It works about the same but initiates scripts when files or directories are modified or otherwise manipulated.  However, it won't work recursively to monitor a hierarchy all at once.

---

### Post by sim085 on 2014-04-02
Ok I will have another look at rsync. I did not look too much into it because I thought this was meant to back up with a remote repository which is not my case. All I would like is to backup on another drive keeping folder structure if possible (maybe compress too?)

---

### Post by Lars Noodén on 2014-04-02
rsync does that nicely, it can also do snapshots, but it cannot compress.  For compression, you could use tar or dump but then you're looking at re-copying the contents of the entire hierarchy fresh each time the script is run.  That is probably undesirable.  

Basic rsync is from source to destination.  The first time will be slow.  Then any subsequent runs will copy only the changes.

```

rsync -av /home/foo/ /mnt/backup/foo/

```

If you want to remove files from the destination that no longer exist on the source, then use the --delete option in addition.  See also --dry-run.  Check the manual page for the full description of what those do and for a complete list of all features.  There may be some others that you find useful.  

If you want incremental backups using rsync, there are quite a few tutorials so you have a choice in finding one that makes sense to you or is close to the results you want.

---

