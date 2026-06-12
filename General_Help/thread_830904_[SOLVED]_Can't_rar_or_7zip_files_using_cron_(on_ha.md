---
title: "[SOLVED] Can't rar or 7zip files using cron (on hardy)"
date: 2008-06-16
forum: General Help
---

### Post by kewlito on 2008-06-16
Hi, this is my first post, and I'll ask you for help with something that's driving me nuts. I'm trying to set up a server that takes care of the backup of many other machines. The expected behavior is that it mounts a share, makes a local copy of the important files, and then it rars the new files.

I made various scripts and each of them is intended to backup a particular machine. The problem is that none of them work.

I'll go into detail:

[LIST]
[*]I've tried using the full binary path.
[*]The cron jobs are run as root.
[*]I've tried using the system crontab (/etc/crontab) as the root crontab (sudo crontab -e).
[*]There are no dots or other special characters in the script names.
[*]The machine is an Ubuntu Alternate 8.04 with all the updates as of today.
[*]All the scripts are with 777 permissions.
[*]The scripts run fine if ran manually using sudo.
[/LIST]

The rsync part is ok, the local copy of the files is perfectly updated. The problem is when making a rar (or 7zip, I've tried modifying the script to make a .7z, when I first noticed this). Cron makes an 8kb file that's corrupted. I mean, the file that I want is there, with the correct name, but without content. If a touch a file in the line after the archiving, the touch is done.

I thought it could be a permissions problem, but common sense says that it is impossible, as the script is run as root.

Well, I think I've covered all the bases, feel free to ask me for any further information, and thanks in advance if you're able to help me in any way.

---

### Post by kewlito on 2008-06-16
Further info:

I've put root as well as my user in */etc/cron.allow*
If I put only the archiving line in the script, it doesn't work, but I still wanted to tell about all the other stuff just to put you in context.

---

### Post by bingoUV on 2008-06-16
Questions : 
1. Do you run the rar/7zip command on the server (the machine running cron job) or the client (from which you get the data)?

2. This corrupted file (that your rar/7zip from cron is creating) might have a lot to say about the problem. I guess if it is 8kb, it won't be empty. Run the following commands to be sure , and post the output here if you do not understand : 
```

file /path/to/corrupted/file
ls -l /path/to/corrupted/file
vi /path/to/corrupted/file

```

I wrote vi above rather than nano because the file could be a binary file and I trust vi more than nano about handling binary files securely. Type :q<Enter> to quit vi.



Cron debugging tips :
1. Suffix your command by  ">> /path/to/error/log 2>&1". For example if you are calling a script /path/to/script, add the entry as (ignore the time entry)
```

1 2 3 * * * /path/to/script >> /path/to/error/log 2>&1

```

After the time to run the script is passed, examine the /path/to/error/log file.

2. Look at the man page of the command you are running and check which environment variable it relies on. echo that variable , it will go into /path/to/error/log so that you know what its value is in the cron environment.

---

### Post by kewlito on 2008-06-16
1 - I'm not sure if I understood well your question, but both machines are the same. I mean, the machine is intended as a backup server, so it pulls the required files (via rsync) from other servers and then archives them, so I can have some backup history. The short answer is that the machine that archives is the one with the cron job, in fact it doesn't archive just when it runs as a cron job, when run manually the rar/7zip is fully functional.

2- I'll try that, I thought about it but then I discarded it because I just thought that viewing the binary-truncated file should be useless to my non-expert eyes

3- I'll try that debugging tip too, and get back to you.

Thanks a lot for you fast response.

---

### Post by kewlito on 2008-06-30
Well, I just added the option to log and it fixed itself, just don't know what happened but now it works. Thank for the help.

---

### Post by machalie on 2010-07-07
I exactly face this problem today.  However I just add the ">> /path/to/error/log 2>&1" and the problem is solved.  Don't know what is happen.

Orignal:
7z a /backup/monthly/$file.7z /var/lib/ldap /var/lib/mysql /data/svn /data/trac
Change to:
7z a /backup/monthly/$file.7z /var/lib/ldap /var/lib/mysql /data/svn /data/trac >> /backup/monthly/$file.log 2>&1

---

