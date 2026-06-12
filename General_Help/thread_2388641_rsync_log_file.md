---
title: "rsync log file"
date: 2018-04-05
forum: General Help
---

### Post by grangemd-3 on 2018-04-05
I am trying to use rsync to backup my files.  I have it working but I am trying to add a log file so that I can verify if everything synced.  I came across the --log-file option and was trying to use it the only trouble I am having is trying to save the log-file as a date so that as I go along over time I will get multiple log files that I can quickly go back and look at.  Here is my rsync lines I have however when I do this I don't get the date I get random values/numbers as a filename.  

```
Source1=/mnt/user/Videos/TVShows/TVShows/Battlebots
Destination1=/mnt/disks/BackupB1/Test

#Make the log file
now=$(date +"%F-%T")
echo "$now" > /mnt/user/BackupLogs/DailyTimes.txt

rsync -avh --delete --stats --log-file=$BAKPATH/"$now" --link-dest="$Destination1"/Daily1/ "$Source1"/ "$Destination1"/Daily0/

```

---

### Post by TheFu on 2018-04-05
Which interpreter is being used?  It is usually specified in the 1st line.  Without that, it will pick up the current shell, but when run by cron, that might not be bash, so the bash-specific stuff will fail.

I don't see BAKPATH set, so getting garbage seems lucky.  Often, quoting files is done around the entire path+filename. "$BAKPATH/$now"

I'd use that quoting method around all the other options, as needed too.  If you use #!/bin/bash -x on the first line, you can see what is being interpreted in each line. Also, don't underestimate the power of an "echo" before any command that doesn't seem to work as you think it should.  

Not that it should matter, but is there a reason you aren't using rsnapshot?  It uses hardlinking with rsync. Which also has me asking why use --delete when you are hardlinking for versions?  I'm confused.

I would strongly recommend ensuring that the backup storage mount was actually performed too.  I've been burned.  Best to verify the mount.

The manpage says:```

              Note some versions of the popt option-parsing library have a bug
              in  them  that  prevents  you from using an adjacent arg with an
              equal  in   it   next   to   a   short   option   letter   (e.g.
              -M--log-file=/tmp/foo.   If  this  bug  affects  your version of
              popt, you can use the version of  popt  that  is  included  with
              rsync.
```
Doesn't look like an issue, but maybe it is?

What is the return code from rsync?  Manpage shows what they mean.

---

### Post by oldfred on 2018-04-05
I do use date, but differently.

In my rsync script, I backup several files and add date. Paths already exist.

```
# So I know additional sources and ppas
cp /etc/apt/sources.list ~/Documents/LinuxDocs/CurrentSys/z170/sources.list.backup_$(date '+%Y-%m-%d_%H:%M:%S')_$(hostname).txt
#ls -l /etc/apt/sources.list.d/
cp /etc/apt/sources.list.d ~/Documents/LinuxDocs/CurrentSys/z170/sources.list.d.backup_$(date '+%Y-%m-%d_%H:%M:%S')_$(hostname).txt
# List of all installed applications
dpkg --get-selections > ~/Documents/LinuxDocs/CurrentSys/z170/ubuntu_files_$(date '+%Y-%m-%d_%H:%M:%S')_$(hostname).txt

```

On my own trim file, I do this:
      ```
 #!/bin/sh
# trimSSD
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
# fstrim -v /home >> $LOG 


```

fred@Z170N:~$ echo "* $(date -R) *"
* Thu, 05 Apr 2018 14:11:06 -0400 *

---

### Post by TheFu on 2018-04-05
The ':' isn't allowed on NTFS, is it?

---

### Post by grangemd-3 on 2018-04-05
> **TheFu said:**
> Which interpreter is being used?  It is usually specified in the 1st line.  Without that, it will pick up the current shell, but when run by cron, that might not be bash, so the bash-specific stuff will fail.

I don't see BAKPATH set, so getting garbage seems lucky.  Often, quoting files is done around the entire path+filename. "$BAKPATH/$now"

I'd use that quoting method around all the other options, as needed too.  If you use #!/bin/bash -x on the first line, you can see what is being interpreted in each line. Also, don't underestimate the power of an "echo" before any command that doesn't seem to work as you think it should.  

Not that it should matter, but is there a reason you aren't using rsnapshot?  It uses hardlinking with rsync. Which also has me asking why use --delete when you are hardlinking for versions?  I'm confused.

I would strongly recommend ensuring that the backup storage mount was actually performed too.  I've been burned.  Best to verify the mount.

The manpage says:```

              Note some versions of the popt option-parsing library have a bug
              in  them  that  prevents  you from using an adjacent arg with an
              equal  in   it   next   to   a   short   option   letter   (e.g.
              -M--log-file=/tmp/foo.   If  this  bug  affects  your version of
              popt, you can use the version of  popt  that  is  included  with
              rsync.
```
Doesn't look like an issue, but maybe it is?

What is the return code from rsync?  Manpage shows what they mean.

Sorry I had a bunch of other junk in my code so I was trying to copy and paste the more important information and I guess I missed a few things.  I will just post it all so I don't miss anything

```
#!/bin/bash 
##Perform backup from Finalizer to Backup Disks and log


Source1=/mnt/user/Videos/TVShows/TVShows/Battlebots


Destination1=/mnt/disks/BackupB1/Test


#Make the log file
now=$(date +"%F-%T")
echo "$now" > /mnt/user/BackupLogs/DailyTimes.txt
current=($now.log)
echo "$current" >> /mnt/user/BackupLogs/DailyTimes.txt
BAKPATH="/mnt/user/BackupLogs"


#####################
### Destination 1 ###
#####################


### Source 1 ###
rm -rf "$Destination1"/Daily5
mv "$Destination1"/Daily4 "$Destination1"/Daily5
mv "$Destination1"/Daily3 "$Destination1"/Daily4
mv "$Destination1"/Daily2 "$Destination1"/Daily3
mv "$Destination1"/Daily1 "$Destination1"/Daily2
mv "$Destination1"/Daily0 "$Destination1"/Daily1
(date +"%F-%T") >> /mnt/user/BackupLogs/rsync.log
rsync -avh --delete --stats --log-file=$BAKPATH/"$now" --link-dest="$Destination1"/Daily1/ "$Source1"/ "$Destination1"/Daily0/ 
(date +"%F-%T") >> /mnt/user/BackupLogs/rsync.log

```

---

### Post by SeijiSensei on 2018-04-05
I just use "rsync -av" and direct the output to a file with ">> logfile".

```
sudo rsync -av SOURCE TARGET >> logfile
```

---

### Post by TheFu on 2018-04-05
For backups of media/large files, I use rsync -avz. Don't really want 60 versions of a 1+G file.

For backups of system or personal files, I rdiff-backup - it handles all the versioning stuff for us.  Most backup tools will do the versioning for you. Don't know if that is something you would consider or not.  rsync drops some things that might be important when you use hardlinks - like how ownership and permissions change.

The most recent backup from rdiff-backup looks just like an rsync, BTW. To restore, you can use rdiff-backup -r, or rsync or just cp the file(s) back (as root to maintain correct ownership/permissions).

---

