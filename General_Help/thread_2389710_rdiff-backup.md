---
title: "rdiff-backup"
date: 2018-04-20
forum: General Help
---

### Post by Quarkrad on 2018-04-20
I have a couple of questions on rdiff-backup I cannot find an answer to. Without going into detail, I only need 1 or 2 versioned copies - how do you limit the number of versions created (what is the addition to the script)? Last question - I have managed to link rdiff-backup with systemd so my backup happens when I shut down. This is working OK using the command **rdiff-backup /home/dad/.mozilla /media/dad/backup/rdiff** - what I would like to do is amend the script so that I backup .thunderbird as well as .mozilla? Any help appreciated.

---

### Post by TheFu on 2018-04-21
rdiff-backup has manpages which are extremely thorough.  It is always best to check the manpage on your system, since that will have the information for the exact version of the command you have installed, unless webpage versions.

Backups are performed using 1 rdiff-backup command.
Removal of older versions are performed using another rdiff-backup command.  I think the option is "--remove-older-than"
 Post #25 [https://ubuntuforums.org/showthread.php?t=2365338](https://ubuntuforums.org/showthread.php?t=2365338)  has examples.

BTW, 2 versions seems really low.  Since only data that changes gets included in backups, and that data is the diff-gz type, it is pretty tiny. Having 30-60 days of backups is only 10-15% more storage than the original.  30 days really is my minimum.

Only backup browser and email stuff? Why not the entire HOME? Having to redo settings kinda sucks, IMHO.  Also, I'd specifically exclude backing up cache files and "special files" like pipes and FIFOs and devices.   

The rest of that linked thread has some fairly excellent discussions about backups.

---

### Post by Quarkrad on 2018-04-24
On my 16.04 machine I have been playing around with a script in lib/systemd/system/backup.service.  (The backup.service script points to a bash script in home/dad/bin called backup that uses rdiff-backup to copy a file from Downloads to Pictures).  This is purely a test setup - eventually I will copy ~/home to a backup disc.  This backup.service scripts works in virtualmachine 1:

```
[Unit]
Description=Shutdown backup
DefaultDedendencies=no

[Service]
Type=oneshot
ExecStart=/home/dad/bin/backup

[Install]
WantedBy=systemd-halt.service systemd-poweroff.service
```

When I look in Pictures I see the copied file and a folder called rdiff-backup-data

I then create a duplicate virtualmachine and tried the whole thing again but it didn't work - so I amended the backup.service script and it worked. The amended script is:

```

[Unit]
Description=Shutdown backup
DefaultDependencies=no

[Service]
Type=oneshot
RemainAfterExit=true
ExecStart=/home/dad/bin/backup

[Install]
WantedBy=multi-user.target

```

This also works but .....  in Pictures there is the copied file and the folder rdiff-backup-data which has two icons on it, a cross and a lock.  The folder is owned by route.  My question is - in normal circumstances, when using rdiff-backup should the rdiff-backup-data folder be owned by the user or root?

---

### Post by TheFu on 2018-04-24
Depends on which userid is being used to  create the backups.  If root, then root. 
There is nothing magical about rdiff-backup. It doesn't have special escalation rights - and shouldn't.

Putting backups into a HOME is usually a poor choice.

BTW 
home/dad/bin and /home/dad/bin are VERY different. Leading / matters almost always.

---

