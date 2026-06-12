---
title: "Grsync doesn't run via Cron"
date: 2020-01-22
forum: General Help
---

### Post by raccoonstrait on 2020-01-22
Good day all:

Running Xubuntu 18.04 and have set up Grsync and Cron to do weekly backups for two NAS drives (usb) to two other drives attached to the same machine (usb). The Grsync commands (two different profiles) run when run from Grsync. I get an email saying the commands have run via Cron (as well as a daily email telling me Clam has updated). However, when looking at the dates for the Grsync logs, I know they have not run. I then run them manually and the Grsync logs update properly.

Cron Commands:
```

0 22 * * 2 grsync -e "Disk01"


0 22 * * 3 grsync -e "Disk02"

```

Grsync Commands
```

rsync -r -t -p -o -g -v --progress --delete --ignore-existing -s /mnt/Disk01 /mnt/Disk01-BU


rsync -r -t -p -o -g -v --progress --delete --ignore-existing -s /mnt/Disk02 /mnt/Disk02-BU

```

Cron Log Output:

```

Jan 21 21:17:01 username CRON[26680]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 21 22:00:01 username CRON[26830]: (user) CMD (grsync -e "Disk01")
Jan 21 22:02:04 username anacron[26841]: Anacron 2.3 started on 2020-01-21
Jan 21 22:02:04 username anacron[26841]: Normal exit (0 jobs run)

```

I have also tried using the grsync -e "Disk01" on the command line, and it worked. So I am at a loss as to why this is not happening.

Any thoughts?

RacconStrait

---

### Post by norobro on 2020-01-22
When you run 'grsync -e Disk01' from the cmd line does the app window pop up and then close? If so, the problem is that cron runs as root and does not have access to a display.

What you should do is copy the rsync commands into your crontab, i.e.:```
0 22 * * 2 /usr/bin/rsync -r -t -p -o -g -v --progress --delete --ignore-existing -s /mnt/Disk01 /mnt/Disk01-BU
```

What you can try is this:```
0 22 * * 2 export DISPLAY=:0; grsync -e "Disk01"
```

---

### Post by raccoonstrait on 2020-01-22
Thanks norobro

I will give that a try, set for noon today, about 12 minutes, so I should have an answer soon.

RaccoonStrait

Well, that didn't work, and while a file planted to get backed up didn't, it also doesn't create a log file.

RaccoonStrait

---

### Post by norobro on 2020-01-22
Hmm. Please post your last crontab entry. 

I downloaded Grsync to try it out and the command with "export DISPLAY=:0;" works fine here. In backing up a small directory I see a gui window flash. ```
15 17 * * * export DISPLAY=:0; grsync -e test_session
```

I don't see where you are telling it to generate a log. Grsync is just a graphical frontend for rsync and the commands you posted above don't contain the "--log-file=FILE" option (man rsync).

The only way I see to generate a log is to add "--log-file=/some/user/writable/path/grsync.log" to "Additional options:" box under the "Advanced options" tab. Seems the location of the log file does have to be writable by the user. ```
rsync -r -t -v -s --log-file=/home/user/grsync.log /home/user/test /data
```

---

### Post by raccoonstrait on 2020-01-23
norobo,

My apologies, I tried your first suggestion, and that did not work. Since you mentioned that cron ran as root I tried putting the user name in the cron expression, which not only did not help, it through out a security error. After your second reply, I took a closer look at your second suggestion, and to my shame, it worked (that is after I also removed the username. The cron expression that worked looks like this:

```

[FONT=monospace][COLOR=#000000]0 22 * * 2 export DISPLAY=:0; grsync -e "Disk01"

[/COLOR][/FONT][FONT=monospace][COLOR=#000000]0 22 * * 3 export DISPLAY=:0; grsync -e "Disk02"
[/COLOR][/FONT]
```[FONT=monospace]

I did notice that the GUI showed up when these ran (I used different time and date to get faster feedback).
[/FONT]
BTW, grsync log files can be found in /home/username/.grsync. Check grsync /file/preferences and tick both enable logging and if you wish overwrite logs.

Thank you for your time and effort.

I will mark this solved.

RaccoonStrait

---

### Post by kevdog on 2020-01-23
As other user pointed out -- why are you running grsync which is a graphics front end for rsync from a cron job?  Why not just run the command for rsync directly?  Which user is running this sync command? root or normal user?

---

### Post by raccoonstrait on 2020-01-23
kevdog,

Primarily because I found several references to Grsync and Cron when looking for ways to automate the process. Grsync offers ways to test the process more easily than rsync, especially when there are several terabytes involved with the backup. Let us say more easily for me as the list of rsync options is extensive and for me confusing.

Thanks for your suggestion though.

RaccoonStrait

---

