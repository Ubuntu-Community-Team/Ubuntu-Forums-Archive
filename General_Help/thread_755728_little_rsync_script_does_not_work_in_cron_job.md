---
title: "little rsync script does not work in cron job"
date: 2008-04-15
forum: General Help
---

### Post by gian on 2008-04-15
hello All,

I am trying my first script ever, so please allow me some stupid questions.

I am backing up our home folders from a remote server, and have read permissions to do that except for Mail folders.

I have these lines in backup.sh in my home folder of the remote, backup server:

mv *.log *.old
rsync --log-file=vib_home.log -av --delete --exclude=".*/" -e "ssh -i .ssh/rsync-key" gian@server-2007:/home/ vib_home/

Backup.sh is in my Cron table, and gets executed, however:
- existing log file is not renamed to .old
- files are not synchronized 

Here is the log report:
2008/04/15 02:00:29 [6482] receiving file list
2008/04/15 02:00:29 [6482] rsync: opendir "/home/gabri/Maildir" failed: Permission denied (13)
2008/04/15 02:00:29 [6482] rsync: opendir "/home/enzo/Maildir" failed: Permission denied (13)
2008/04/15 02:00:29 [6482] rsync: opendir "/home/enzo/Mail" failed: Permission denied (13)
2008/04/15 02:00:29 [6482] rsync: opendir "/home/enzo/Desktop" failed: Permission denied (13)
2008/04/15 02:00:29 [6482] rsync: opendir "/home/francesco/Maildir" failed: Permission denied (13)
2008/04/15 02:00:29 [6482] rsync: opendir "/home/deborah/Maildir" failed: Permission denied (13)
2008/04/15 02:00:29 [6482] rsync: opendir "/home/deborah/mail" failed: Permission denied (13)
2008/04/15 02:00:29 [6482] rsync: opendir "/home/lost+found" failed: Permission denied (13)
2008/04/15 02:00:29 [6482] rsync: opendir "/home/william/Maildir" failed: Permission denied (13)
2008/04/15 02:00:29 [6482] rsync: opendir "/home/faxmaster/Maildir" failed: Permission denied (13)
2008/04/15 02:00:29 [6482] rsync error: errors with program diagnostics (code 13) at log.c(230) [receiver=2.6.9]

The first backup, obtained manually launching ./backup.sh, worked out fine.

What am I missing ?!

thanks for your time,
-Gian

---

### Post by dsnyders on 2008-04-15
It looks like a permissions problem.  When you run backup.sh manually, you have the appropriate rights.  But when cron runs, it is not using the same permissions.(I'm assuming that you're not running backup.sh as root, right?)  Check your crontab file to see if you are using the correct username.

---

### Post by matey3 on 2008-04-15
did you use chmod 755 for your script? may be it is not executable?

---

### Post by gian on 2008-04-16
backup.sh is 700.

The cron job itself works, because each morning my log files change date.
Also, there is another rsync line that copies two files from another server, and that works fine.

It's like if, after the initial permission errors, the script aborted.

I just found out that mv does not work with wildcards.

---

