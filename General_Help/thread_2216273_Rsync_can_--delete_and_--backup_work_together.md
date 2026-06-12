---
title: "Rsync: can --delete and --backup work together?"
date: 2014-04-11
forum: General Help
---

### Post by vasa1 on 2014-04-11
I have this code in my *crontab*:

```
30 * * * * bash -c 'rsync -lrtv --delete --backup --suffix="."$(date +\%H\%M) --protect-args --modify-window=1 --files-from=/home/vasa1/Dropbox/rsync-include.txt / /media/vasa1/TOSHIBA\ EXT/BACKUP/ &> /home/vasa1/"$(date +\%I_\%M)"rsync.log'
```
Previously, it was the same but without **--backup --suffix="."$(date +\%H\%M)**.

Even now, the basic operation seems to be fine except that I see some backups in the destination that I don't understand. For example:
```
-rw------- 1 vasa1 vasa1     1476 Apr 11 08:42 vids
-rw------- 1 vasa1 vasa1     1568 Apr 10 08:55 vids.0930.1030
```
I'm guessing the issue is with **--suffix="."$(date +\%H\%M)**. (The **%** has to be escaped for the crontab to work.)

I know that one hour ago, I had **vids** and **vids.0930** but not **vids.0930.1030**.

Any idea how I should get:
```
vids
vids.0930
vids.1030

```rather than
```
vids
vids.0930.1030
```?

I suppose I could identify and delete such files periodically using *find*'s *delete* option, but is there a better way to have both *--delete* and *--backup* work together?

---

