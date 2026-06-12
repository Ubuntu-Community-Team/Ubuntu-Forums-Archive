---
title: "Ubuntu o/s &amp; apps backup question"
date: 2015-09-28
forum: General Help
---

### Post by ra7411 on 2015-09-28
This pertains to just a single desktop computer w/ only Ubuntu 14.04 on it.   I want to backup the o/s and various apps, only.  

 I'll keep all the user files that I've created backed up on a separate HD using GRsync. 

If the HD the o/s and apps are on fails, I'm really only trying to avoid the bother of reinstalling the o/s and apps and various settings.

I don't want to use Clonezilla. I think there's a dd terminal command that can do this, but I'm in the dark past that.

Is there a guide on how to do this, or can somebody  furnish a guide?

Thanks

---

### Post by DK1993 on 2015-09-28
Here is the DD command and how it works:
```
 sudo dd if=/dev/sda | bzip2 > /media/usb/image.bz2 
```
Essentially you can change the compression type to whatever suits your needs and where you want the "image" to be saved. 
This guide here [https://help.ubuntu.com/community/DriveImaging#Backup_with_dd](https://help.ubuntu.com/community/DriveImaging#Backup_with_dd) explains it in greater detail. However, an inherent weakness of this is that the resulting "image" is going to be the size of the actual drive, not the OS and apps.

---

### Post by Bucky Ball on 2015-09-28
Be *_very careful_* using the dd command. It takes no prisoners, there is no going back once you hit enter, there is no 'Are you sure you want to ...' message. Once you hit the button it will completely wipe what is on the target you have set before moving the data you want to move there. So be _very, very sure_ you have selected the correct target. dd has a few nicknames, one is 'delete and destroy', which is exactly what it does. We've seen some carnage here.

@DK1993: When advising people to use dd it is a good practice to warn them of the potential dangers of it. This ain't no ordinary backup tool. It is very powerful, yes, but can be devastating for the unsuspecting. 

Having said all that, dd will copy partitions fine. Just be careful. There are other options.
___

Clonezilla is another option which can backup a partition or a whole drive. It also need the target partition to be the same size as the source partition, regardless of how much data is in there (about the only way around this is to shrink the source partition prior to cloning). 

Home site:
[http://clonezilla.org/](http://clonezilla.org/)

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)
___

Lately I've been using fsarchiver which you can install from the repositories. This will save just the data so the target partition need not be the same size as the source partition (from memory). There are others if you have a quick look about online. Good luck. :)

---

### Post by QIII on 2015-09-28
I just added "Please double- or even triple-check your target device to avoid such catastrophic loss." to the warning after the Introduction.

:)

---

### Post by ian-weisser on 2015-09-28
> **ra7411 said:**
> If the HD the o/s and apps are on fails, I'm really only trying to avoid the bother of reinstalling the o/s and apps and various settings.

I keep a human-readable journal of critical applications and settings for that purpose. It reduces the bother to a minor admin task. Trivial to backup and recover (or print out), and re-installing customizations can be simple copy-and-paste.

By delegating that admin task to automated tools you risk more serious disruption when the the automated tool fails at the worst time, when a setting is deprecated, or when an application gets abandoned by the developer and dropped from Ubuntu entirely. Any problems may become much more complex.

Also, your usage (and ideas of what to backup) many change over time, or you may wish to prune away old experiments and other cruft.

---

### Post by ra7411 on 2015-09-28
I'm the original poster, I have the o/s on a 2tb HD, and my backup HD is 1tb, so even if I wanted to image the  whole 2tb hd, I couldn't.

In W8.1 it was pretty easy to image the o/s and apps so you could recover quickly from a corruption or HD failure. I used Acronis and it was uncomplicated and easy.
I'm just wondering why Linux doesn't have something at least as good.

I've got my user files backed up - maybe I should just keep my Ub install disk handy, and in the unlikely case of a problem, just reinstall the o/s and apps and re-configure. Do other people see it that way?

---

### Post by Bucky Ball on 2015-09-28
I see that you should do a backup of your / partition where your OS lives, one way or the other, on a regular basis. Your install breaks, smack a copy back on and you should be up and running in no time. :)

---

### Post by oldfred on 2015-09-28
I find re-install to be easy. But I regulaly install each versions, often several times, but keep the LTS version as my main working install.
So I backup /home, some settings/files from /etc like my grub settings I customize, and a list of installed applications. Since I install regularly I scripted a lot of my reconfiguration after install and keep looking for ways to add any manual edits I have to do. I now need about an hour for a install & reconfiguration. Most is some setting I forgot I needed and was not in my script.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)

Most that want a clone use clonezilla.
       
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]https://help.ubuntu.com/community/CategoryBackupRecovery
[/URL]
 [http://clonezilla.org/](http://clonezilla.org/)
fsarchiver
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page) 

      
 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603](http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
of course, do the dry run first 

 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

      
 Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)
Sample rdiff file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
[http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)

     
 
     
[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]
[/URL]

---

### Post by ra7411 on 2015-09-28
> **ian-weisser said:**
> I keep a human-readable journal of critical applications and settings for that purpose. It reduces the bother to a minor admin task. Trivial to backup and recover (or print out), and re-installing customizations can be simple copy-and-paste.

By delegating that admin task to automated tools you risk more serious disruption when the the automated tool fails at the worst time, when a setting is deprecated, or when an application gets abandoned by the developer and dropped from Ubuntu entirely. Any problems may become much more complex.

Also, your usage (and ideas of what to backup) many change over time, or you may wish to prune away old experiments and other cruft.

That makes sense. I just wrote a text doc w/ the apps  I've settled into using, and I copied my Tbird mail profile, over onto the backup disk. I have Chrome all synced up - no problem w/ a reinstall there.
Doing a ground up reinstall of Windows and apps was always a masochistic task to have to do - a backup was basically neccesary.

I don't think a reinstall of Ub and apps is on the same bad order. Maybe just let the Ub o/s backup ride....... ?

---

### Post by Bucky Ball on 2015-09-28
I use Luckybackup (in the repos) for specific directory backup and Clonezilla or fsarchiver for the Ubuntu / partition. I don't backup Windows as I use it for maybe an hour or two a year and any personal data created is saved on a shared NTFS partition (which is backed up in Ubuntu with Luckybackup). :)

---

### Post by ian-weisser on 2015-09-28
> **ra7411 said:**
> I don't think a reinstall of Ub and apps is on the same bad order. Maybe just let the Ub o/s backup ride....... ?

A full from-scratch reinstall over my (rather slow) connection takes me approximately two hours:
 - 45 minutes to download the latest .iso and create a LiveUSB.
- 45 minutes to install the base system using the freshly-create LiveUSB.
- 15 minutes to restore my backed-up /home data from remote server.
- 15 minutes to restore my applications and customizations from my journal.
- Finally reboot.

If you have a much faster network connection, you can reduce that to one hour or less.
If you use Ubuntu Core or Ubuntu Server for a headless system, just a few minutes.

---

### Post by ra7411 on 2015-09-28
> **ian-weisser said:**
> A full from-scratch reinstall over my (rather slow) connection takes me approximately two hours:
 - 45 minutes to download the latest .iso and create a LiveUSB.
- 45 minutes to install the base system using the freshly-create LiveUSB.
- 15 minutes to restore my backed-up /home data from remote server.
- 15 minutes to restore my applications and customizations from my journal.
- Finally reboot.

If you have a much faster network connection, you can reduce that to one hour or less.
If you use Ubuntu Core or Ubuntu Server for a headless system, just a few minutes.

Maybe I'll just make a recurring calendar reminder to update my iso install disk every April and October (new LTS release), and if and when my o/s gets corrupted or HD fails, just do a new install. I have a decent DSL, and when I installed a couple weeks ago I was surprised at the speed of things, compared to Win installs, and the app installs went really nicely compared to the aggravations of hunting up disks and typing in proof numbers. 
Also, there's no guarantee that I'm not going to botch an image backup, or waste more time trying to figure out exactly what I'm supposed to do to get my image to re-create what I backed up - I don't work with this stuff regularly.

---

### Post by ian-weisser on 2015-09-28
> **ra7411 said:**
> every April and October (new LTS release),
**Regular** releases of Ubuntu, supported for only 9 months, occur every April and October (14.10, 15.04. 15.10, etc).
**LTS** releases of Ubuntu, supported for 5 years, occur ONLY in April of even-numbered years (12.04, 14.04, 16.04, etc).
Some flavors of Ubuntu run a very different LTS schedule.

Your update notifier can be easily set to notify you of either kind of release...or you can simply wait until you need it, then create a LiveUSB on a different machine.
I don't keep a Live USB handy. I have only needed one three times in 10 years.

---

