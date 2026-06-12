---
title: "Using rsync to backup"
date: 2019-05-02
forum: General Help
---

### Post by modomobo on 2019-05-02
I've been using **rsync** to backup my HDDs on an Ubuntu 18.04 server.

```
rsync -aAHXWv --info=progress2 /media/sourceDisk/ /media/backupDisk/  --exclude='/lost+found'
```

It works fine, but if I delete files on the source disk, this doesn't seem to get mirrored on the destination disk.

Basically, I want the backupDisk to just mirror the sourceDisk.

I see there are a bunch of **--delete** options, but I don't really understand what they do.

Any suggestions?

---

### Post by TheFu on 2019-05-02
They delete any files on the target that aren't on the source.  Some delete before mirroring a directory. Some delete after mirroring a directory and some delete as they go.

rsync is a good tool for this "mirroring" requirement.

But if you need backups, might I suggest using a tool designed to do versioned backups?  The command will look almost the same.

```
$ rdiff-backup --exclude='/lost+found' --exclude-special-files /media/sourceDisk/ /media/backupDisk/ 
```

The last backup looks like a mirror of the source.  Diffs are stored inside a subdirectory by date as gzipped diffs. It is very efficient and also stores the metadata for each file and directory in the versioned data.  rsync loses owner and group permission changes over time.  rdiff-backup doesn't.  To restore, you can either get the current mirror with cp or rsync or you can use ```
rdiff-backup -r now /media/backupDisk/  /media/sourceDisk/ 
```  The "now" specification can be almost any time - to prevent confusion, I use yyyy-mm-dd for the spec, but I bet "last week" or "last month" would work too.  

Doesn't that use lots and lots of storage? Nope.  30 days of daily, versioned, backups, usually require just 10% more storage.  60 days usually needs 15% and 90% days 20-30%. It depends on the amount of changed files and the sizes for those files.  Versioned backups help to address crypto-locker malware and if your system is hacked, then you can see which files changed on which days.  That is extremely handy.

---

### Post by TheFu on 2019-05-02
From the rsync manpage:```

            --del                   an alias for --delete-during
            --delete                delete extraneous files from dest dirs
            --delete-before         receiver deletes before xfer, not during
            --delete-during         receiver deletes during the transfer
            --delete-delay          find deletions during, delete after
            --delete-after          receiver deletes after transfer, not during
            --delete-excluded       also delete excluded files from dest dirs
```

'receiver' is the name for the target directory.  rsync is a client/server tool, so the source and/or target can both refer to remote storage on other computers.
If you are tight on space for the target partition, then --delete-before  is probably what you want.  If you want the safest deletions, use --delete-after.

---

### Post by modomobo on 2019-05-03
Hey, this is really helpful &#8212; thanks!!

---

