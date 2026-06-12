---
title: "get rid of xp partition in 15.04 dual boot and reuse whole drive"
date: 2015-06-06
forum: General Help
---

### Post by Stanley_Pickens on 2015-06-06
Howdy all,

I read in a post asking how to do this, 

get rid of xp partition in 15.04 dual boot and reuse whole drive,  

and the user was asked to repost for instructions using the following method -->> 

Clone your Ubuntu partition (with fsarchiver or in this case clonezilla will do as well) then reformat your hard drive and restore the clone.

Where can I find info on how to go about this.

Thanks,

---

### Post by oldfred on 2015-06-06
You can also do what this user did with gparted. Erase XP after backing up any data you want, and move Linux partition left. Also need good backup of Linux partition(s) as any interruption in process will corrupt it.
[http://ubuntuforums.org/showthread.php?t=2280786](http://ubuntuforums.org/showthread.php?t=2280786)

I have not used Clonezilla, as it is too easy to just reinstall, but I do backup /home & other settings so I can quick restore system. Many like Clonezilla as it is a full image of system.

       discussion of alternatives/strategy backups
[URL="https://help.ubuntu.com/community/BackupYourSystem"]https://help.ubuntu.com/community/BackupYourSystem

[/URL]
 [http://clonezilla.org/](http://clonezilla.org/)

[URL="https://help.ubuntu.com/community/BackupYourSystem"]
[/URL]

---

### Post by leunam12 on 2015-06-06
> **oldfred said:**
> 

I have not used Clonezilla, as it is too easy to just reinstall...
[URL="https://help.ubuntu.com/community/BackupYourSystem"]
[/URL]

So, what are your tricks for re-installing that make it so easy? I dread having to re-install since I haven't kept track of all the programs that I have installed and all my customizations.

---

### Post by oldfred on 2015-06-06
I have been installing the alpha, beta versions regularly into another partition or two. After doing it a couple of times I realized I was doing the same thing over & over. I learned command line way to do many things & then just copied history and made a bash file. 
I also use a separate /mnt/data partition which I link into every install so my data, Firefox & Thunderbird profiles are all the same. I back data partition up separately. I also in rsync backup of /home which is not large include an export of the list of installed apps and system configuration from bootinfoscript.

My backup plan is so I have everything I need to reinstall.
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

---

### Post by grahammechanical on 2015-06-06
So, the re-install part is easy. It is the backup and restore part that takes a bit of thought. :)

Regards

---

