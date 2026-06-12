---
title: "Cron job issue with external hard drive"
date: 2015-10-03
forum: General Help
---

### Post by ric_Poirier on 2015-10-03
Hi,

Two days ago, I started a cron job to backup my home folder (/home/myusername/) to an external hard drive (/media/myusername/backup1). Here is how I set it up:

```
sudo crontab -e
```

I need to access the sudo crontab because some files in my home folder require this.

```
0 3 * * * rsync -arv -delete /home/myusername/ /media/myusername/backup1/
```

So everyday at 3:00 AM, this job should run. Yesterday morning, I checked if everything had been synced and all was fine. This morning though, there was a problem.

I first noticed that my hard drive containing the root folders (I have a separate one for my home folder) had become really big. Analyzing if with the df command showed me that the problem was located in the /media folder. In the /media folder, there were two subfolders: /media/myusername/backup1 AND /media/myusername/backup11.

It seems the job has ignored backup1 and created an new backup11 subfolder (I checked, there was no typos in the cron job).

Do you have any idea about what could have caused this?

Thanks,

---

### Post by TheFu on 2015-10-03
a) how is the external disk mounted? You want to use the fstab or autofs, not anything tied to your GUI login. Basically, YOU need to decide where this storage should be mounted, don't let the OS make up the location.  /Backups is what I use on my backup server. /media is for "*removable storage*" according to the Linux Filesystem Hierarchy Standards. [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure)

b) crontabs like this really should be put into a script and just the script called from the cron. That way you can more easily follow scripting best practices. [http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting) has a list. Plus a good backup script is usually more than 1 line. Mine for this netbook is ... 161 lines (including comments). Part o my script validates that the specific storage is mounted where it should be - otherwise, filling / with backups for 20 systems would be bad.  Of course, the script didn't start out that way - I added it after an "issue" happened.

c) A mirror might not be a sufficient backup strategy. What happens if the source file is corrupted or accidentally deleted and nobody sees this before the next backup?  It will be bad.  Versioned backups are very important. I keep between 30 and 120 days of backups per system. How long depends on how critical the data is AND how big a target the machine is. rdiff-backup is an amazing tool, very similar to rsync, but designed for backups.   
[https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/) is the best, shortest, complete, how-to for rdiff-backup.

d) Be certain to setup the remote ssh root login to only allow key-based authentication.  Plus it is better to "pull" backups than to push them.  On the same machine, this isn't important. 

IMHO. There are 600 different ways to do this. Whatever works for you is "best", by definition.  At least for today.

---

### Post by ric_Poirier on 2015-10-03
TheFu,

Thanks for your reply. I will check out the links you included.

a) Using fstab should solve my issue. You are right, it is probably a mounting issue.
b) Interesting, I will read on that.
c) I realize that. I will look at your link. The major problem I am facing is space. My home folder often is very big from downloads.
d) What?

Regards,

---

### Post by TheFu on 2015-10-03
c) backup media files separately from email, documents, and any code repos.  For media files, use rsync. For everthing else, use rdiff-backup.  Also - my "backup script" cleans out all the crap and excludes trash, cache, and any media files. BTW, I keep media files outside the HOME so all this stuff is easier.

d) Backups on the same machine are a security issue. If the box gets hacked, having the backups on a different machine could be the difference between having a backup and having nothing. The key-based authentication is for putting those backups over the network onto another machine.  rsync, rdiff-backup and pretty much **every** other backup tool for Linux (with a few exceptions) will use ssh for these network transfers BY DEFAULT. ssh security is important and part of that is preventing remote root access completely.  [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)  Perhaps you aren't needing this yet. You will.

ssh is an amazing tool - [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh) shows about 10 things that ssh can do, securely, with very little risk, if properly secured. Basically, your home machine can be available from anywhere in the world - that's files, desktop, calendar, media, anything.

---

