---
title: "Rsync script problem"
date: 2006-10-09
forum: General Help
---

### Post by Lunar_Lamp on 2006-10-09
I use the following script to backup my home dir (sorry for the huge amount of comments):

```
#!/bin/sh

# rsync.sh
#
# - this script will back up /home/ed using rsync to maxtor hdd
# 
# - can be executed by user (no need for sudo/root access)
# 
# 
#Some explanation of the various rsync flags (info from rsync's man page):

# -v: verbose - this flag makes rsync tell you what files it's moving and gives 
a summary at the end
# -u: update - this forces rsync to skip any files for which the destination file already exists and has a date later than the source file 
# -r: recursive - rsync will mirror the directories you specified and all the directories inside them.
# -t: times - rsync will copy all the timestamps of the source files, so that the files on the external drive are exact replicas.
# --progress: rsync will tell you how many files need to be copied before it's finished. this is useful if you want to see what's going on.
# --delete: this tells rsync to delete any files on the receiving side that aren't on the sending side.
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo " Backing up home directory, this may take some time depending on how long 
it was since you last backed up..."
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"

rsync -vurtpL --progress --delete --exclude=.kde/cache-PMSEH/ --exclude=.wine/ --exclude=.opera/cache* --exclude=.Trash/ --exclude=.icons/ /home/ed /media/maxtor/backups/home-backup

echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "All done!"

```

Basically, the line that does the magic is:

```
rsync -vurtpL --progress --delete --exclude=.kde/cache-PMSEH/ --exclude=.wine/ --exclude=.opera/cache* --exclude=.Trash/ --exclude=.icons/ /home/ed /media/maxtor/backups/home-backup
```

I was under the impression that the "--delete" parameter would delete files in the destination folder that were not in the source (i.e. if I delete something in my home folder when I next sync with my backup, the file will be deleted from my backup).  This is not happening with this script.

What am I doing wrong?  Is it the "u" option that conflicts with the "--delete" option?

---

### Post by Lunar_Lamp on 2006-10-10
Nobody has any ideas?

---

### Post by jimbren on 2006-11-01
did you get anywhere with this?

I have something similar going on with my backups.

---

### Post by Lunar_Lamp on 2006-11-01
I'm afraid not, however I shall be looking into it again soon - i.e. when I get some time to sit down and think in the next couple of days.  If I solve it I shall report back here what my solution was!

---

