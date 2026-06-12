---
title: "Cloning SSD to external HDD for security"
date: 2015-06-02
forum: General Help
---

### Post by MantasJ on 2015-06-02
Hello, I have spent last couple of weeks heavily modifying my Ubuntu 15.04 and I don't want to do it again if I mess things up. I have installed Ubuntu 15.04 on 840 EVO 120gb SSD (only about 30gb is used) in UEFI mode and I want to clone whole SSD to an external HDD so later I can do full recovery and start from the beginning. I am new to linux scene and I am not sure where to begin and what is the best way to do this. Looking for guidance.

---

### Post by oldfred on 2015-06-02
Those that want full clone often suggest Clonezilla.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

But a clone is obsolete as soon as you start to use system, but can be a starting point.

I prefer to backup /home which has all your user settings, perhaps some settings in /etc that were system settings. I actually copy anything I manually edit in /etc like grub or other files into /home so I only backup /home.  And of course all your data needs to be backed up, but that also normally is in /home.

An image backup also copies a lot of temporary and log files that you do not need.
      
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

