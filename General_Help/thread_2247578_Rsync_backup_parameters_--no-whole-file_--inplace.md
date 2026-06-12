---
title: "Rsync backup parameters: --no-whole-file --inplace"
date: 2014-10-09
forum: General Help
---

### Post by Kirkx on 2014-10-09
I'm trying to fine tune Rsync parameters to do daily data files backup from a hard disk partition to USB hard disk (both Ext4). Here is the command:

```

rsync -avh --delete --progress /media/xyz/source/ /media/xyz/target

```

I'm not sure about the whole concept of "delta-transfer algorithm" and -W parameter (--whole-file). I have come across all kinds of pros and cons of using the three parameters listed below. Would it be a good idea to add any of them to my command:
--whole-file
--no-whole-file
--inplace

Here is an excellent Rsync help page:

[http://www.computerhope.com/unix/rsync.htm](http://www.computerhope.com/unix/rsync.htm)

---

### Post by TheFu on 2014-10-09
When I need to know details about the rsync, I use 
a) the rsync manpage
b) [https://rsync.samba.org/](https://rsync.samba.org/)

if you watch the files being transfered, they are put into temporary locations until the transfer is completed. Then the full file is moved to the correct name AFTER. This is safer than writing directly to the file location, but if the storage is tight (or for very large files that will not be accessed during the xfer), it may desirable.

Rsync, as you are using above, is not really the best back method for anything other than large media files that don't change often (i.e. just a mirror), IMHO.  For documents and settings, using versioned backups make much more sense - rdiff-backup is the tool for that - there are others. [http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) is the best, easiest, reference for that tool. The command is similar to rsync, but provides much more in terms of recovery options AND takes very little extra backup storage to have 30 days of incremental backups.

Of course, this all depends on what is being backed up.

For large media files, I use this:
```
ionice rsync -av --stats --progress "$SRC" "$TGT"

```
No compression, because they are already compressed.

---

