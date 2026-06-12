---
title: "What is this script actually doing"
date: 2020-04-26
forum: General Help
---

### Post by Alligator on 2020-04-26
Below is a script which backups my entire drive, /home and /. I want to make sure the /home is backed up, because I believe that I have multiple copies of 18.04.  This is on a new computer and should be fast but its not.  Check out the second file when I tried to find nvidia-xconfig. A new video card was needed. I understand the rsync command. The HD is 1.5T and 91% full, way more than the original computer.  I need to find a different repair shop. LOL 
```

#!/bin/sh
#
#
# This is a backup script from The Computer Clinic
# Please run this with the sudo command!!!

 
location=/*
# destination=/media/8362bd63-ecfa-4b26-8abb-3c5b1355465a/
destination=/Back_up/

echo
echo "ATTENTION: Please run using the sudo command. exp sudo ~/usb_backup_script.sh"

while :
do
        if [ -d $destination ]
        then
                break
        else
                echo
                echo "The Linux Backup external drive is not mounted, please investigate"               
                read junk
                exit 1
        fi
done

#       rsync -axz --dry-run --delete --exclude=/proc --exclude=/sys \
#                                        --exclude=/mnt --exclude=/media \
#
# Use --dry-run to simulate cmd and use --log-file=/tmp/backupshit.txt to check for errors

        rsync -rltDvzu --progress --delete --delete-excluded --exclude-from=backup.lst \
        $location $destination

        echo "Changing Permission, please wait..."
        chown -R ron:owner $destination

```

find nvidia-xconfig.
```

/Back_up/Back_up/home/ron/Desktop/media/md0/media/8362bd63-ecfa-4b26-8abb-3c5b1355465a/usr/lib/nvidia-340/bin/nvidia-xconfig
/Back_up/Back_up/home/ron/Desktop/media/md0/media/8362bd63-ecfa-4b26-8abb-3c5b1355465a/usr/bin/nvidia-xconfig
/Back_up/Back_up/home/ron/Desktop/media/md0/usr/bin/nvidia-xconfig
/Back_up/home/ron/Desktop/media/md0/media/8362bd63-ecfa-4b26-8abb-3c5b1355465a/usr/lib/nvidia-340/bin/nvidia-xconfig
/Back_up/home/ron/Desktop/media/md0/media/8362bd63-ecfa-4b26-8abb-3c5b1355465a/usr/bin/nvidia-xconfig
/Back_up/home/ron/Desktop/media/md0/usr/bin/nvidia-xconfig
/home/ron/Desktop/media/md0/media/8362bd63-ecfa-4b26-8abb-3c5b1355465a/usr/lib/nvidia-340/bin/nvidia-xconfig
/home/ron/Desktop/media/md0/media/8362bd63-ecfa-4b26-8abb-3c5b1355465a/usr/bin/nvidia-xconfig
/home/ron/Desktop/media/md0/usr/bin/nvidia-xconfig

```

---

### Post by TheFu on 2020-04-26
[https://explainshell.com/](https://explainshell.com/) can be used to see what most commands are doing.

The last line with chown probably doesn't do something you want.

i would check for a mount using the ... er ...  mount command.

i think rsync is the wrong tool for backups for a number of reasons.

---

### Post by Alligator on 2020-04-27
Thanks for the assistance, particularly the website.  I missed the /mnt - LOL I been away from Linux for about 20 years now, still hate Windows .  What would you suggest rather than the rsync cmd?

---

### Post by ActionParsnip on 2020-04-27
Good that you checked your backup, make sure it's OK

---

### Post by TheFu on 2020-04-27
> **Alligator said:**
> Thanks for the assistance, particularly the website.  I missed the /mnt - LOL I been away from Linux for about 20 years now, still hate Windows .  What would you suggest rather than the rsync cmd?

rdiff-backup, duplicity, and there are a few others.  They do versioned backups AND capture owner, group, permissions, ACLs, and some get xattrs too.  These are all important at restore time.  There are example scripts in these forums. Search and you will find them.

---

### Post by Alligator on 2020-04-27
Thanks again.  I deleted a HUGE file called Back_up from the root directory.  LOL

---

