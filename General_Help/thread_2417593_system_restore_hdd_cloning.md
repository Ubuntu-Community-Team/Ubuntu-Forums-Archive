---
title: "system restore? hdd cloning?"
date: 2019-04-24
forum: General Help
---

### Post by jebi on 2019-04-24
Hi,
 
Is there an Ubuntu / debian version or windows system restore?
 
Also something even better something that clones an hdd / or hdd partition so that it could be restored?

something with a gui would be best...
 
thx

---

### Post by Rodney9 on 2019-04-24
Timeshift or Grsync in the software center, tutorials and reviews on google

---

### Post by oldfred on 2019-04-24
Many alternatives for backup, depending on what you want.
       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636) 
    
       If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
More backup info from 1clue
[https://ubuntuforums.org/showthread.php?t=2377810](https://ubuntuforums.org/showthread.php?t=2377810)
[https://askubuntu.com/questions/569679/whats-a-good-back-up-strategy-for-1-desktop-pc](https://askubuntu.com/questions/569679/whats-a-good-back-up-strategy-for-1-desktop-pc)

---

### Post by TheFu on 2019-04-25
I've been meaning to write up a multi-part blog article about backups which starts simple and ,with each following article, different aspects would be addressed, to protect against different issues.

But just to keep this short, the quickest answer for single-system backups is:
```
$ sudo mkdir -p /Backups/`hostname`
$ sudo rdiff-backup    --exclude-special-files      --exclude   /Backups     /       /Backups/`hostname`
$ sudo rdiff-backup    --remove-older-than 60D       /Backups/`hostname`

```

Pretty simple. It gets everything, probably much more than you want.  Be careful with the spacing. I've exacgerated the spaces above. Don't have spaces where I don't explicitly show any or things will break.

In general, the total storage needed for the backup storage area will be 1.1x - 1.3x the size that the original storage is using for 30-90 days of backups. 
So a 10G minimal desktop would need 13G of backup storage. Bargain!
Or a 50G normal desktop install would need 65G to have 60 days of versioned backups. 
These are worst case estimates, assuming you keep media files backed up separately.

Having backups on the same system you are trying to protect is a bad idea. Crypto-locker loves connected storage. Don't use Samba, or NFS to connect backup storage either.  The "best practice" is to "Pull" the backups from a storage server where you keep the backups and lock down all network access so only connections FROM the server to other systems are allowed.  It shouldn't be used as a NAS or media server, ideally.  But we all live in the real world and have to manage risks as best we can.  Nobody is perfect.

I don't use the script shown above. It gets much more data than needed - but everyone has to start somewhere.  I've posted elsewhere  in these forums some tweaks for my backup strategy.

Please don't use tar or zip or plain rsync for backups. They were designed in a different time.  rdiff-backup is basically rsync, but using steroids specifically designed for backups. rdiff-backup commands look almost identical to rsync commands, so if you plan to use rsync/grsync or any other flavor of that tool, just jump to rdiff-backup. You won't regret it.

Some newer tools have been coming out like borgbackup.  My data is more important than the hardware it sits on and I don't want to risk it with tools that still have known issues.  When a developer warns you this is "alpha code", we need to listen.

If you just can't use the shell, I suppose something like **aptik** is what you really want.  I tried to use it and didn't like it. It was too simplistic.

**Back-in-time** is another option. I used it for Mom's computer for a few years and it worked great for her personal files, but there are limitations. I wouldn&#8217;t use it for system-level backups.  

The built-in backup tool for Ubuntu is DejaDup.  This is based on Duplicity, which checks all the boxes for an excellent backup tool. Why not just select it?  Search these forums for people who are seeking help with corrupted backups.  Actually, you should do that for any backup tool. I'm not smarter than lots of people here, but I have been around as a Unix/Linux admin a long time. I've learned that when people have corruption issues with backup tools and it isn't a single person, something else is happening. There is something about the tool that is confusing or leads to backups which cannot be restored.

If you insist on having an image solution, fsarchiver is probably the most flexible. No GUI, sorry.  I've used it about 20 times. It always worked, but it works on the partition level, which can be VERY cool, or too complex.  Just depends on your skills.  For things like tiny systems running on Raspberry Pi computers, I use it.

Anyway, good luck. Don't fear the shell. ;)

---

