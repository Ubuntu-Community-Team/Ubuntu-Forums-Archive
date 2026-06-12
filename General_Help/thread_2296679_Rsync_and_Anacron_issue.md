---
title: "Rsync and Anacron issue"
date: 2015-09-28
forum: General Help
---

### Post by Lappert on 2015-09-28
Running Kubuntu 14.04.

I have rsync set up on anacrontab where my virtualbox file (Win7-32.vdi) is backed up to our offsite server once a week.

The line in anacrontab reads:

7    120    rsync.local.virtualbox        nice rsync -avz --delete --include=Win7-32/ /home/user/VirtualBox\ VMs /opt/rsync-virtualbox | mail -s "Rsync Local home-user" [EMAIL="me@mydomain.com"]me@mydomain.com[/EMAIL]

This and other similar lines work rather well. The problem appears to be in that the directory name holding the file has a space in it, i.e., "VirtualBox VMs"  When we set up the virtualbox, it didn't occur to us that would be an issue. But for a number of reasons we'd prefer not to fix it by putting in a hyphen or underscore -- either being an obvious fix.

In any case, I'm getting email on what occurs during the rsync:

```
rsync: link_stat "/home/user/VirtualBox" failed: No such file or directory (2)
rsync: link_stat "/VMs" failed: No such file or directory (2)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1183) [sender=3.1.0]
```

I thought we handled the space in the directory name by putting in a backslash, i.e., "VirtualBox\ VMs". A number of linix pages suggested this was the way to handle this.

I'd appreciate any help or suggestions. Thank you.

---

### Post by TheFu on 2015-09-28
Try using a quote - remove the escaped spaces ("\ ") when you do this.
In the future, you've learned a valuable lesson. Don't use spaces in names, because not all programmers write code to handle it properly.  
Another thing is to always use lowercase for machine hostnames for a similar reason. Not every programmer handles mixed case names correctly - especially if a comparison is needed. Most of the time it isn't a problem, but sometimes it is. I didn't try this, but ... 

```
nice /path/to/rsync -avz --delete --include="Win7-32/"  --include="/home/user/VirtualBox*VMs" /opt/rsync-virtualbox
```  
Never trust the PATH in cron.
There are also  **--include-from=FILE** options. Have you tried that?

BTW, for backups, rsync is great for a 1-time mirror, but not sufficient for versioned backups. Use rdiff-backup for that need. [https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/)  The most recent backup is a mirror, just like rsync.  Older versions are compressed diffs off that. Keeping 30 days add about 10% more storage - highly efficient.

---

### Post by ajgreeny on 2015-09-28
> **TheFu said:**
> In the future, you've learned a valuable lesson. Don't use spaces in names, because not all programmers write code to handle it properly.  
It's an unfortunate result of the default folder that VBox makes when you install it that all VMs end up in that folder with a space.

It would make life so much easier for we Linux users if they could put an underscore in place of the space, but just like Lappert I did not do this, and now with 10 VMs in the folder it is just too much palaver to rename the folder and have to make changes to all the VM's settings so I live with it.

---

