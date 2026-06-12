---
title: "[SOLVED] My script doesn't run correctly from crontab"
date: 2007-02-12
forum: General Help
---

### Post by tribble222 on 2007-02-12
I want to backup my files daily with rdiff-backup.

I am using a slightly modified version of the script provided here [http://www.ubuntuforums.org/showthread.php?t=356604](http://www.ubuntuforums.org/showthread.php?t=356604)

When I execute the script from the terminal ($ sudo sh dailybk.sh) it executes perfectly.

When I add the command to the root contab ($ sudo crontab -e) it executes when it should but only backs up a couple directories before it exits.

So I added

logfile="/home/tribble222/Desktop/backup_script.log"
cp /dev/null $logfile

to the top of the script and strategically placed: echo "text here" >> $logfile , echo "text here2" >> $logfile, etc. throughout my script so I could debug it.

Looking at the logfile it seems the script was executing completely, without error.

So then I added a ">> $logfile" to the main command of the script (sudo rdiff-backup -v5 --print-statistics $EXCLUDE $INCLUDE $SOURCE_DIR $TARGET) so that every single directory it is backing up is written to the logfile.  When I did this and ran the script from crontab, it executed perfectly and completely!  (also creating a giant logfile in the process!).

I don't understand how simply having it create a giant log of everything it backs up could cause it to work.

Anyone know what might be going on?  It seems the cron doesn't know to wait for the rdiff-backup command to complete unless I tell it to create the log...

---

### Post by koenn on 2007-02-12
I dont know much about cron, but maybe you could put the backup command in the background (add & at the end of the command line) so it doesn't interfere with or get interference from other activity / cron jobs ? 

if you do that, add "exit" at the end of the script so it doesn't keep just hanging there when completed.

---

### Post by dcstar on 2007-02-12
> **tribble222 said:**
> .......
Anyone know what might be going on?  It seems the cron doesn't know to wait for the rdiff-backup command to complete unless I tell it to create the log...

Possibly the extra log data is slowing down the process enough to avoid some sort of condition which causes it to exit when you aren't logging.

You may want to experiment with the "nice" command to reduce the job's priority and see if that makes any difference.

---

### Post by tribble222 on 2007-02-13
Thanks for the suggestions.  Unfortunately either making it run in the background (&) or "nice-ing" it didn't do anything to change its behaviour.

Maybe someone knows a better way to debug why it is not completing?  Is there a way to make cron run my shell script in a terminal?

---

### Post by tribble222 on 2007-02-13
Okay I got it working.  It's not really a fix but a workaround.  I lowered the verbosity from 5 to 3, so it only writes a few lines to the log (4 or higher writes all the files it copies to the log).  That way I get a small log but the script still works correctly.

---

