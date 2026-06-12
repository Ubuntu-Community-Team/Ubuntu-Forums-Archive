---
title: "I don't know how to do a backup of my O.S"
date: 2020-03-26
forum: General Help
---

### Post by madetosuffer on 2020-03-26
Hi, 

I'm from Brasil, so, sorry for my probably weird English on some parts.

I got the Ubuntu Budgie 19.10 last week and I came from the windows 10 that usually turned my computer useless. I loved the Ubuntu interface and how fast my computer became with it, but I'm a dumb with it and have none experience with this OS. I passed a few days trying to create a new partition for a backup of my entire O.S. and ,believe, I'm very proud of myself to get on Gparted and get a new partition by Boot with a pen-drive( yeah, hi-tech bros ahaha). OK, stage 1 complete!

So after, i started Tilix and tryed some commands on it. I tried the dd (Dungeons&Dragons) command, but i have some difficult to understood the "if" and "of" commands and how to get the image and backup after if I have some problem... So i decided to search more on the web for more methods and stuff, I found two programs for it, the SystemBack (ppa) and Clonezilla, but, how to get this programs? I don't know how to get this from the web and i tried some tutorials that doesn't work any more( I think cause they are obsolete or something like). Please, help me how to get a backup of my OS, I need a backup before trying to use and learn more the linux Ubuntu OS, I'm just a newbie :(

---

### Post by oldfred on 2020-03-26
Many have different ways to backup Linux based system.
Some like full image backup, but that is obsolete in just a few minutes and since larger many then do not keep it updated.
Some of us just want our data backed up as Ubuntu can easily be re-installed. So then no real reason to backup Ubuntu.

Most Software with Ubuntu is in the repository. You then can just download using command line, synaptic or Software Center. 

discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)

If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[https://ubuntuforums.org/showthread.php?t=2368992&](https://ubuntuforums.org/showthread.php?t=2368992&) 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

Also different backup processes may depend on whether you are just a home user if little change in data daily, or a business that needs daily or even more frequent backup processes.

I am a home user, and backup weekly. Have multiple flash drives for backups using rsync. I also manually copy some most critical data to DVDs. And have a copy of my data on another drive which really is not a backup as if I delete or change a file the copy on drive also has that change, but no way to go back and find older version.

---

### Post by HermanAB on 2020-03-27
In general, there is not much point in backing up Linux.  It is already backed up at thousands of universities and ISPs around the globe and it only takes about 30 minutes to install the latest and greatest version afresh.  Therefore, the much more efficient method is to back up only your data.  If you have a very special server, then you can make a backup of /etc which is where all the configuration files are, for future reference.

See this:
[https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

---

### Post by madetosuffer on 2020-03-27
Thanks! 

I'm just a home user, a university student user, that will use the computer just for files as documents, university programs, spotfy and etc...not for gamming and other stuff. I love the options for backup information, specially the rdiff-backup, and i tried to put this on worth, but, yeah, still a newbie and that was too hard for me. So i decided use the Déjà Dub app.

thank u all for the support! Speacially Oldfred. I read all the links u guys gave to me :D

---

