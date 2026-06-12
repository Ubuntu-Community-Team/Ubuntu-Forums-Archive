---
title: "Change partition type..."
date: 2015-09-16
forum: General Help
---

### Post by timgood on 2015-09-16
Hi Guys - I have a large hdd with Ubuntu Gnome installed on /dev/sda1 and an extended partition /dev/sda2 which is split into /dev/sda5 (swap) and /dev/sda6 on which I have Kubuntu installed. I am hoping I will be able to delete /dev/sda1 and extend the Kubuntu partition to take up the entire drive, leaving swap as it is. Would this be possible or am I looking at re-installing? Thanks in advance for any advice. [ATTACH=CONFIG]264446[/ATTACH]

---

### Post by yancek on 2015-09-16
It's possible with GParted from the Ubuntu installation medium.  The first thing is, which system is booting?  Are you using Grub from Ubuntu or from Kubuntu?  If it is Kubuntu that saves a problem.  If it is Ubuntu, you will need to boot Kubuntu and install it's Grub to the MBR.  The problem with this method is that is fairly risky as you will be moving all the system files as well as the location of the boot files to a different sector and I would not expect Grub to boot until you changed this.  Moving partitions is a slow process in addition to being risky as is anything when working with partition modification.

Simpler method since you already have a large partition for Kubuntu would be to create a mount point for sda1 in Kubuntu and format that partition and use it for data,

---

### Post by oldfred on 2015-09-17
I agree with yancek's suggestion.

I also prefer smaller system partitions such as 25GB for / and then large data partition(s) or separate /home.
You also should be backing up /home & a list of your installed applications to make it easy to reinstall if you ever have major issues.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[URL="http://ubuntuforums.org/showthread.php?t=1901437"]http://ubuntuforums.org/showthread.php?t=1901437

[/URL]
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]https://help.ubuntu.com/community/CategoryBackupRecovery
      [/URL]
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folder]("http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders")      [ ]("https://help.ubuntu.com/community/CategoryBackupRecovery")  [ ]("http://ubuntuforums.org/showthread.php?t=1901437")

---

