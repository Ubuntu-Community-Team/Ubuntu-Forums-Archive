---
title: "Backup /home using rdiff-backup"
date: 2018-05-17
forum: General Help
---

### Post by Quarkrad on 2018-05-17
I'm having trouble with the actual syntax to backup **/home** to a local HD.  I can achieve this using **rsync -aP --exclude=.* /home/$USER/ /media/$USER/backup** - this is OK but I would also like .mozilla .thunderbird and perhaps .config. (Up to now I have been using gadmin-rsync that copies the whole of **/home** but I would like to use rdiff-backup because of versioning).  I have tried various rdiff-backup options but keep coming up against a permission issue.  Although this does not work, ideally I would like something like **rdiff-backup /home/username /media/username/backup** Any advise on what would work greatly appreciated.

---

### Post by TheFu on 2018-05-17
```
sudo /usr/bin/rdiff-backup  --exclude-special-files /home/username /media/username/backup
```
is probably what you want.  The /media storage should be linux too, not NTFS.  Really, it should be mounted using a proper mount, not gvfs, to have correct ownership and performance.  gvfs (mounted through a GUI)  is slow.

Backups should almost always be run as root to ensure ownership/group/permissions are correctly included too.

I would grab a few other places on the system and capture some system information as part  of the backups too.
* /etc/ ... tiny, but full of system tweaks you might make.
* /usr/local ... there non-package installs should go.
* apt-mark .... grab the current list of packages installed automatically and manually.  These can be used during a restore to get your system back to what you like fairly quickly.  Just be certain to store the output somewhere that also is included in your backups.

And don't forget to remove old backups using /usr/bin/rdiff-backup --remove-older-than to keep only as many versions as you have storage to support.   Generally I keep 60 days for low-risk systems and 120days for high risk servers.  Using the full path to  programs inside scripts is a best practice, BTW.

---

### Post by Quarkrad on 2018-05-17
Wow - that did it; can not thank you enough.  A few questions if I may:
1. Where can I read about the **/usr/bin/** part?  I've never seen this and I don't quite understand why adding this makes it work.
2. The output I got was:
```
dad@dad-VirtualBox:~$ sudo /usr/bin/rdiff-backup  --exclude-special-files /home/dad /media/sf_shared/backup
[sudo] password for dad: 
Warning: hard linking not supported by filesystem at /media/sf_shared/backup/rdiff-backup-data
dad@dad-VirtualBox:~$ 
```
I've seen this hard linking message before - on my system **sf_shared/backup** is on another ext4 internal HD. All references I've read about this hard linking message is where the end file system is fat or ntfs.

I'm testing this on a virtualbox system (ubutnu mate 16.04) - hence sf_shared/backup.

Ultimately I would like to run this at shutdown and have 'sort of' got that bit sorted - I just need to put this code into my script and it should work (tested with a small file set).  However, backing up **/home** will take a little longer so I might have to play around with my systemd service scripting. A concern at the moment is - if I get the systemd part to run is there a way to get over the sudo/entering password bit?  May be this is show-stopper in terms of 'just shutting down and it all happens' (the backup that is).  I might just have to run this manually and then shutdown the pc.

---

### Post by TheFu on 2018-05-17
Virtualbox shared storage doesn't honor all Unix storage commands. Also, I've had issues with it failing for file locking.  IMHO, it is a toy and shouldn't be used.  If you want to share storage between systems, use NFS.

If you want automatic backups, use cron.  No sudo then  - assuming you either use /etc/crontab or root's crontab. After a thread here (perhaps with you?) last month??? .... I modified my backups on a laptop to put the system into standby after all the daily backups ran.  Those happen just after midnight.

As for the /usr/bin, that is basic knowledge that was missed somehow.  Relative vs absolute paths. People coming from Windows often do not have this background, so they miss out on lots of stuff. BTW, Windows also uses it, but Windows as a system decided that the added security risks for their dirty solution was worth it to reduce hassles. Almost any beginning Unix book or training would cover this.   In my Linux classes, right after people get a logon, we cover paths. Also, when putting anything into a script, always, always, always use the absolute path for all programs.  Cron and other automation systems do not provide the same environment as a normal userid session login does.

---

