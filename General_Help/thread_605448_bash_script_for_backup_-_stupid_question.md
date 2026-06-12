---
title: "bash script for backup - stupid question"
date: 2007-11-07
forum: General Help
---

### Post by viz_e on 2007-11-07
Hi.
I have written a small shell script that backs up my home folder.

```

#!/bin/bash
# Backup data

# Rsync log
OUTPUT=/home/viz/.rsync_bck

# Keep 14 incremental backups
BACKUPDIR=snapshots/`date +%a`_`date +%P`

# Kind of standard options, including svn-auxiliary files removal.
OPTS="-vazhutC --stats --stats --backup --backup-dir $BACKUPDIR --delete-excluded"

# Backing up
echo "Starting backup: `date +%c`" >> $OUTPUT

rsync /home/viz $OPTS --exclude="viz/.mozilla/firefox/*/Cache/*" --exclude="viz/.Trash"  --exclude="viz/vari" --exclude="viz/Documents" --exclude="viz/iso" --exclude="viz/Nexuiz" --exclude="viz/google-earth" --exclude="viz/tmp" --exclude="viz/.googleearth" --exclude="viz/.icons" --exclude="viz/.java" --exclude="viz/tifi" --exclude="viz/free" --exclude="viz/.adobe" --exclude="viz/.kde/share/icons"  --exclude="viz/.thumbnails" --exclude="viz/Puppy" --exclude="viz/.local/share/Trash"  --exclude="viz/.texmf-var" --exclude="viz/.texmf-config" --exclude="viz/TestGmail" --exclude="viz/.mozilla-thunderbird/wxfgxqxr.name with space/News" 
--exclude="viz/.mozilla-thunderbird/wxfgxqxrname with space/ImapMail"
username@server:/home/username/Backup >> $OUTPUT 2>&1

echo -e "Backup done: `date +%T`\n\n ***** \n" >> $OUTPUT

```

I have two non-vital questions about the above code:

1. The last line ```
echo -e "Backup done: `date +%T`\n\n ***** \n" >> $OUTPUT
``` prints also "-e" in the file. How can I get rid of it? If I execute the same line by typing it in a shell it does not happen.

2. I tried many different combinations of {} "" '' \(space) and so on to collect all the --exclude options in a variable, but rsync seems not to be able to recognize the spaces in the directory names.

Any thoughts on this?

Thanks

---

### Post by Micah Elliott on 2007-11-07
> **viz_e said:**
> 
1. The last line ```
echo -e "Backup done: `date +%T`\n\n ***** \n" >> $OUTPUT
``` prints also "-e" in the file. How can I get rid of it? If I execute the same line by typing it in a shell it does not happen.


You might want to double check that you're running the *real* echo in your script: /bin/echo , and not something else that might have shown up in your PATH/aliases/functions/etc.

> **viz_e said:**
> 
2. I tried many different combinations of {} "" '' \(space) and so on to collect all the --exclude options in a variable, but rsync seems not to be able to recognize the spaces in the directory names.


rsync accepts a "--exclude-from=FILE" option that may be more flexible.

---

### Post by viz_e on 2007-11-08
> **Micah Elliott said:**
> You might want to double check that you're running the *real* echo in your script: /bin/echo , and not something else that might have shown up in your PATH/aliases/functions/etc.

You are right. In this way it works just fine.

> **Micah Elliott said:**
> 
rsync accepts a "--exclude-from=FILE" option that may be more flexible.
Yes, I have thought about that. I just wanted a solution that was "self-contained", in the sense that you have only the script and no other external file. This is of course not a real issue, though. ;)

Thank you for your help! :lolflag:

---

