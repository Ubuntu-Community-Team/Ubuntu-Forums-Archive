---
title: "cron.daily job doesn't run"
date: 2016-05-18
forum: General Help
---

### Post by cathect2 on 2016-05-18
I have a bash script that performs a simple backup of my /home folder. I placed the script in my etc/cron.daily folder. But it doesn't run.

The script, called "mybackup," is here:

```

 #!/bin/bash 




#######################
#
# Crappy Backup Script
#
#######################


# BACKUP /HOME


set -e 


LOGFILE=/home/sc/Backup.log


notify-send Backup "Backing up your files..."
#


rsync -a --delete --exclude='.dbus' --exclude='.gvfs' --exclude='.cache' "${HOME}" "/media/Backup/Home/" && echo "$(date "+%m%d%Y %T") : Backup Completed" >> $LOGFILE 2>&1;
#
notify-send Backup "Your Backups Are Complete."



```

This code runs as expected in terminal. 

1. The script has 755 permissions.
2. The script's name does not have a period in it.
3. If I issue: **run-parts --test /etc/cron.daily **the script appears in the list.

As far as I know, this should work.

What do I need to do to get cron/anacron to function properly here?

Thank you

---

### Post by Tadaen_Sylvermane on 2016-05-18
Permissions should be 755. Your script currently isn't executable. Also if I may suggest switching to versioned backups. That way instead of making a full backup every day you only backup the changes. Saves boatloads of space on your backup device.

This is what I use for my backups.



```
if /bin/ping -c 1 "$SERVER" ; then
  if [[ -e "$3" ]] ; then
    if /usr/bin/ssh "$USER"@"$SERVER" "[[ ! -e ${4}/${FOLDER} ]]" ; then
      /usr/bin/ssh "$USER"@"$SERVER" "/bin/mkdir ${4}/${FOLDER}"
    fi
    if /usr/bin/ssh "$USER"@"$SERVER" "[[ -e ${4}/${FOLDER}/current ]]" ; then
       # incremental backups, this is the one normally run
       /usr/bin/rsync -"$RSYNCOPT" --link-dest="$4"/"$FOLDER"/current "$3" "$USER"@"$SERVER":"$4"/"$FOLDER"/"$FOLDER"."$NOW"
       /usr/bin/ssh "$USER"@"$SERVER" "/bin/rm -f ${4}/${FOLDER}/current"
    else
        # initial backup, typically runs once
      /usr/bin/rsync -"$RSYNCOPT" "$3" "$USER"@"$SERVER":"$4"/"$FOLDER"/"$FOLDER"."$NOW" 
    fi
    /usr/bin/ssh "$USER"@"$SERVER" "/bin/ln -s ${4}/${FOLDER}/${FOLDER}.${NOW} ${4}/${FOLDER}/current"
    /usr/bin/ssh "$USER"@"$SERVER" "/usr/bin/find ${4}/${FOLDER}/${FOLDER}* -maxdepth 0 -mtime +${DATADAYS} -exec /bin/rm -rf {} \;"
  fi
fi
```

---

### Post by cathect2 on 2016-05-18
Sorry. I meant 755. I have double checked. The file is executable. I've edited my post to reflect.

---

### Post by oldfred on 2016-05-18
I do not know bash, but this is a trim bash file I have used as daily cron job.

```
#!/bin/bash
# trimSSD.sh

LOG=/var/log/trim.log
echo "* $(date -R) *" >> $LOG
fstrim -v / >> $LOG
# fstrim -v /home >> $LOG

```

---

### Post by cathect2 on 2016-05-18
Thank you, @oldfred. I know my backup script is crappy. That's why I named it "Crappy Backup Script." :D What I want to know is why it isn't running...

---

### Post by oldfred on 2016-05-18
Have you tried splitting backup completed to its own line, rsync just may not like it.

---

### Post by cathect2 on 2016-05-18
Just for curiosity I tried this. It works as expected when I run in terminal, but doesn't run as a cron job.

---

### Post by untrustytahr on 2016-05-18
I'm a bit rusty on my cron, but if I recall correctly, files in cron.daily needed to be owned by root (and point to a root file if it's a link) and are run as root.  Maybe $HOME is resolving to /root instead of /home/sc.  Try putting the full path to your home and see if it works.

---

### Post by cathect2 on 2016-05-19
I gave the full path to all of the directories. It runs fine in terminal. But does not run when placed in cron.daily... frustrating.

---

### Post by cathect2 on 2016-05-19
There is an error in the logs: exit status 1.

---

### Post by btindie on 2016-05-19
Few pointers.

cron jobs in /etc/cron.* run as root, meaning that "${HOME}" in your rsync command will expand to '/root' and so it won't do what you expect.

Have you looked in /var/log/syslog if see if CRON ran the command? which I suspect it did.

The notify-send interacts with the desktop but as you'll be running it from cron it won't work. Running a command from the terminal is not the same as from cron which has a limited environment.

If you want to log the fact that a backup has been completed you'd be better of using the 'logger' command which will send the output to syslog, see "man logger".

The "2>&1" is unnecessary as it'll have no affect. echo writes to stdout and nothing will be on stderr
```
echo "$(date "+%m%d%Y %T") : Backup Completed" >> $LOGFILE 2>&1;
```

If you want to capture the output from rsync in case that generates an error use ```
rsync .... &>> $LOGFILE && echo "..."
```
"&>" is short hand for writing " >$LOGFILE 2>&1" with *bash. *The double ">>" causes it to append instead of overwrite the file on output. See 'man bash' and search for "Redirecting Standard Output and Standard Error".

---

### Post by cathect2 on 2016-05-19
Hi@btindie. Thanks for the assist here.

I don't see evidence that cron ran the script in the system log.

I have no doubt that what you say is true here, but it is a bit over my head. Sorry! I was just trying to get an automated backup of my files and was doing the best that I could. My day job is English teacher, so I'm a bit out of my depth here.

1. So, since root runs the script, I can't use ${HOME} but must use the full path to the directories, right? So if I use "home/sc/" root should run it ok?
2. I tried to parse out what you were after, and edited my command this way. But it produces a broken pipe error. What did I do wrong?

```
rsync -a --delete --exclude='.dbus' --exclude='.gvfs' --exclude='.cache' "/home/sc/" "/media/Backup/Home/" &>> $LOGFILE && echo "$(date "+%m%d%Y %T") : Backup Completed"
```

Thanks for your patience...

---

### Post by btindie on 2016-05-19
That's correct $HOME is a variable that is set based on the user it's evaluated under. So for root HOME=/root and user 'sc' HOME=/home/sc. You can see this by opening a terminal and typing "echo $HOME"

You also don't need everything in quotes providing it doesn't contain spaces in which would need to be escaped or quoted. e.g. "+%m%d%Y %T" == +%m%d%Y\ %T

The below should work and you can run it as either your local user or root. You can switch to root by typing "sudo -i" followed by your password. Type 'exit' to leave the root shell.

```
rsync -a --delete --exclude='.dbus' --exclude='.gvfs' --exclude='.cache' /home/sc/ /media/Backup/Home/ &>> $LOGFILE && echo "$(date +%m%d%Y\ %T) : Backup Completed" >> $LOGFILE
```

Before running it, make sure you've set LOGFILE to something.

You can also add the script to your users own crontab. It can be edited with "crontab -e", see 'man 5 crontab'.

---

### Post by cathect2 on 2016-05-19
That should be **/usr/bin/**rsync . . . , correct?

---

### Post by jim_deadlock on 2016-05-19
It might be better to use the rsync --log-file option, and you can also use a file for the excludes:

```
rsync -a --delete --log-file=/path/to/rsync.log --exclude-from=/path/to/skip-these.txt /home/sc/ /media/Backup/Home
```

---

### Post by cathect2 on 2016-05-19
I tried the command suggested by tdindie. Then I tried my revision which used /usr/bin/rsync ... to initiate the script. 

Both fail to run at the time specified in my crontab for cron.daily.

---

### Post by jim_deadlock on 2016-05-19
As btindie suggested, try putting it in your user crontab instead of cron.daily, same result but might be more reliable.

```
crontab -e
```

Set it for a few minutes ahead of now, for testing, eg:

```
5 19 * * * rsync -a --delete --log-file=/path/to/rsync.log --exclude-from=/path/to/skip-these.txt /home/sc/ /media/Backup/Home
```

CTRL-X to save/exit

---

### Post by cathect2 on 2016-05-19
Yes, that does work. I'm still curious why I seem to be unable to get anything to work by placing it into /etc/cron.daily/. That is a much more elegant solution. Thanks for your help.

---

### Post by kjohri on 2016-05-23
There are two commands, cron and anacron. anacron looks at cron.daily. If anacron is not installed cron executes cron.daily at 06:25 AM, and many systems are switched off at that time.

[http://www.softprayog.in/tutorials/anacron]("http://www.softprayog.in/tutorials/anacron")

---

