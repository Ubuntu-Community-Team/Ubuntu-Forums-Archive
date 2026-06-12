---
title: "bash script date/backups"
date: 2013-03-06
forum: General Help
---

### Post by il pepe on 2013-03-06
Hi,
I trying to do a automatic backup (cron) to a network drive. First piece of the code checks whether the drive is smb mounted.
The second part is the actual backup.
I would like to do some kind of incremental backup every day.
Once a month (like the first day of the month) i would like to do a clean backup.
This is the code I wrote up to now:

```

RESULT=$(mount | grep "/Lacie")
#Lacie is my NAS

if ["$RESULT" == ""]
    then 
    echo "Disk not mounted"
    sleep 2s
    else
    echo "Disk mounted"
    if [date +%d == 1]
        rsync -avh --delete --progress /home/pieter/Documents /home/pieter/Mounts/Lacie/backup_pieter/ 
#clean backup: --delete function
    else
        rsync -avh --progress /home/pieter/Documents /home/pieter/Mounts/Lacie/backup_pieter/
#incremental backup, without the --delete
    fi
fi

```

I suppose this thing works? mayby someone can confirm as i'm not sure about the date checking thing.

I'm slowly building and expanding this small script: The next goal is to keep like 2 complete 'clean' backups, and one that is incrementing (the most recent backup).
How would ik script this?

Is it a good idea to put this in one script that is done everyday? or should i build multiple script files?

---

### Post by papibe on 2013-03-06
Hi il pepe.

Here's a few thoughts:

I would use the command 'mountpoint' to check if there's something mount there:
```
if mountpoint -q /home/pieter/Mounts/Lacie; then
    echo "mounted."
else
    echo "not mounted."
fi
```

As for more complex backups, there are several approaches:
[LIST]
[*]for differential you can use the option --compare-dest (see [here]("http://unix.stackexchange.com/questions/25195/how-do-i-save-changed-files")).
[*]for incremental, you can use the combo --backup and --backup-dir (see [here]("http://rsync.samba.org/examples.html")), or use hardlinks (option -h) (see [here]("http://webgnuru.com/linux/rsync_incremental.php")).
[/LIST]
Here's another [guide]("http://www.jveweb.net/en/archives/2011/02/using-rsync-and-cron-to-automate-incremental-backups.html") for full and incremental backups using rsync.

Let us know if you need more help with that.
Regards.

---

