---
title: "Can't update from Ubuntu Gnome 15.04 to anything new like Ubuntu Gnome 16.04LTS"
date: 2017-01-15
forum: General Help
---

### Post by macsociety on 2017-01-15
Hi, finally decided it was time to get past Ubuntu Gnome 15.04 and I get an error message that I can't.

Running my Software Updater it tells me Software Updates are no longer available for 15.04 so I click the Upgrade button in the window and get this error after typing my password and click the Upgrade button on the [COLOR=#000000][FONT=sans-serif]Welcome to Ubuntu 16.04 LTS 'Xenial Xerus' window:

[/FONT][/COLOR]Can not upgrade


An upgrade from 'vivid' to 'xenial' is not supported with this tool.

I also tried doing this in Terminal using the [COLOR=#333333]sudo do-release-upgrade command.

I am hoping I don't have to download 16.04LTS and do a clean install as I don't want to lose all my emails and downloads and such under my current working 15.04, unless there is an option booting from a Install CD and have it to a clean install but keep all the rest of my apps intake and ready to use again on boot with all old emails, etc...

I use Thunderbird Mail for work and don't want to have to set all that up again.

Thanks for any advise on easiest way to upgrade past 15.04.

Thanks

TJ[/COLOR]

---

### Post by howefield on 2017-01-15
Should just be a matter of changing the sources.list to point to [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)

Have a browse here : [https://help.ubuntu.com/community/EOLUpgrades/](https://help.ubuntu.com/community/EOLUpgrades/)

---

### Post by RobGoss on 2017-01-15
Hello and welcome, A clean installation would be the best way to go seeing you're are already having upgrade issue's but I'm sure someone else maybe able to advise if this would be a good option

As far as mail goes does **Thunderbird** mail allow you to backup up your important mail for cases like this? I've only use Thunderbird maybe once just to test it and see how it works

The reason I recommend doing a clean installation is because jumping from one distribution to another, is problematic in most cases

I would not risk loosing everything trying to upgrade your system to **16.04**, I think you're ahead of the game right now so I would make a complete backup and move forward 

I would also recommend making a backup of any important documents and data

---

### Post by itnet7 on 2017-01-16
Macsociety,

The upgrade path for Non-LTS used to only be possible from minor version to next minor version until you reach to the LTS you're wanting to use. The only direct path for 16.04 would be either the previous LTS (14.04) or 15.10. A lot of things have changed over the years, but I would check and ensure that is not the problem you're experiencing. As the previous posters have mentioned (and you may already know this), backup all of your important data before proceeding. Hope this helps. 

itnet7

---

### Post by oldfred on 2017-01-16
You send me mixed message.
You say your data is valuable, but do not have any backups?
Hard drives fail, users make mistakes, laptops get lost, many reasons you really need to have a good backup.
And those that recommend backups say you do not have backup unless you know you can use it to restore your system.

 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery) 

      
 If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

I prefer the rsync option to copy files to other drives & flash drives.
I also copy data to DVDs, so I have older data just in case I change or delete something and it is not in the rsync data.

       
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

---

### Post by macsociety on 2017-01-16
Yes, I back-up.  ;-)

Just was hoping upgrade to newer was easier and kept all I had in place so I did not have to start from scratch on all settings, etc...

Sounds like clean install is in order.

Thanks

TJ

---

### Post by howefield on 2017-01-16
> **macsociety said:**
> I use Thunderbird Mail for work and don't want to have to set all that up again.

> **macsociety said:**
> Sounds like clean install is in order.

If you are doing a clean install over the existing partitions, not marking them for formatting will leave your /home folder intact, so thunderbird and most other configurations will be fine.

Having said that, I'd take a copy of /home before hand anyway :)

---

### Post by macsociety on 2017-01-17
Cool, may try that and see how it goes.  

Was also considering it may be a good time to switch from Ubuntu Gnome to Fedora 25 but.... have to mull it over.  

Thanks for the advice all.  TJ

---

### Post by macsociety on 2017-01-19
Upgraded to Ubuntu Gnome 16.04.1 LTS and all is well.  Clean install and copied all over from backup drive.  ;-)  TJ

---

### Post by RobGoss on 2017-01-21
That's great doing a clean installation is a good move if you have have less stored on your machine it makes a big difference when somethings goes wrong and you have to resort to doing a cleans install.

---

### Post by kurt18947 on 2017-01-22
For the sake of others that may want to do the same thing, there is a Thunderbird add-on, ImportExportTools that can help with moving Thunderbird profiles. It may need to be obtained from non-Thunderbird official sources so use caution if you go that route. I've tried simply copying the .thunderbird folder and editing the .ini file but didn't have success with that.

---

