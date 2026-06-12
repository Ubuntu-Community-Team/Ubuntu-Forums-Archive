---
title: "speed of accessing backups"
date: 2018-10-21
forum: General Help
---

### Post by Bhakti108 on 2018-10-21
Hi, 

I did a full backup today (146Gb) onto a 1TB ext HDD. I then did a complete new install of Ubuntu 18.04. I now want to download some of the files from the backup. using Archive Manager I clicked to open, its now been 20 Mins and its barely 1/3 along the line (see image)

would others consider this is normal speed? my laptop has 16Gb RAM quad core, I have used the terminal to find out what is being used actively, and its less than 2Gb, so I can't see that its the cpu. 

Interested to hear views please. 

Cheers                       [ATTACH=CONFIG]281398[/ATTACH]

---

### Post by dragonfly41 on 2018-10-21
This does not answer your question.
The advice from many pros in this forum is to backup *then verify that you can restore from backup.*
You have missed this important step since you have jumped the gun and installed a fresh OS before verifying your backup works when you need it.
Search this forum using "Advanced Search" and use keyword "backup" in the thread title.

Here is just one of many threads you can read ...

[https://ubuntuforums.org/showthread.php?t=2389631&highlight=backup](https://ubuntuforums.org/showthread.php?t=2389631&highlight=backup)

tar is not recommended as a backup.

---

### Post by dragonfly41 on 2018-10-21
Caveat: I have never used tar as backup so this idea may not work.

But I read from this blog that you can split a large tar and this might work to at least recover data in parts from your archive.

[https://www.tecmint.com/split-large-tar-into-multiple-files-of-certain-size/](https://www.tecmint.com/split-large-tar-into-multiple-files-of-certain-size/)

Hopefully you will receive other advice to dig you out of the hole.

---

### Post by oldfred on 2018-10-21
Tar is very old school and goes back to the days when drives were much smaller. Not now recommended for large images.

I personally hate any archive that is compressed. It goes back to a 3.5" drive that would not read, but I knew it had lots of data. I now use rsync, but some recommend rdiff.
       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636) 
    
       [https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync](https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync)
Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[https://ubuntuforums.org/showthread.php?t=2392127](https://ubuntuforums.org/showthread.php?t=2392127)
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)
Sample rdiff file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
[http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use) 
            Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986) 
    
       If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

