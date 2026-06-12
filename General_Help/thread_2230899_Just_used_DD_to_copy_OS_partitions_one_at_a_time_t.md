---
title: "Just used DD to copy OS partitions one at a time to a backup drive. Good idea?"
date: 2014-06-21
forum: General Help
---

### Post by 777funk on 2014-06-21
I tried Clonezilla but it didn't do what I wanted it to do. I don't need the entire disk, I just need the OS partitions. So I found an easier way but I'm not sure it's a good idea. All I know is it worked! 

I did the following:
1. Gparted - Formatted the target HDD (sdb in this case) to the same GPT partition table as the stock drive that I use. 
2. Gparted - setup partitions as I have them but left a little room for space (maybe 5% larger) in each partition just incase
3. dd if=/dev/sdX1 of=/dev/sdY1 for all 4 OS partitions (in my case boot, /, /home, swap)
4. Marked boot partition with the boot flag

Powered down, Unplugged the stock drive, Plugged in the backup drive and everything booted as if nothing ever happened.

So it worked! Now that it's done (and done carefully since I realize dd can be dangerous if not done with careful attention to drive letters), I figured I'd ask if this was a good (or proper) idea. I've always wanted to try dd and I have good backups of important data so I didn't have much to loose.

---

### Post by HermanAB on 2014-06-22
Howdy,

Well, I won't say that it is completely useless, but the Linux OS is available online, for free, from countless mirror servers, so backing up the OS is not very useful.  One day, when your machine breaks donw and you have to repair it, you would want to install the latest and greatest version of Linux, not an old tired backup.  

Over time, you will find that re-installing linux becomes easier and quick, so I just backup my data and maybe make a tar ball of the /etc directory.

---

### Post by Mark Phelps on 2014-06-22
> I tried Clonezilla but it didn't do what I wanted it to do. I don't need the entire disk, I just need the OS partitions. 

That's because you selected the wrong save option. You want to choose saveparts, not savedisk.  That allows you to select individual partitions to be saved.

---

### Post by oldfred on 2014-06-22
It was my understanding that you should not attempt to dd copy gpt partitions. gpt has much more internal data that must be preserved that also is in gpt partition table. Copy of entire drive as long as drive will not remain mounted in same system is ok.

       Do not use dd to copy partition with gpt due to unique guids & UUIDs post #12 (by the author of gdisk).
[http://ubuntuforums.org/showthread.php?t=1680929](http://ubuntuforums.org/showthread.php?t=1680929)

---

### Post by 777funk on 2014-06-23
> **Mark Phelps said:**
> That's because you selected the wrong save option. You want to choose saveparts, not savedisk.  That allows you to select individual partitions to be saved.

Thanks. I think I saw a save 'part'. I didn't find a way to save more  than one partition. If there is a way to save more than one is there a way  to do them all at once? I'm guessing I'd still have to manually  partition the target hard drive to match? If this is the case, is there  an advantage to run Clonezilla vs doing it in a terminal?

[QUOTE=HermanAB]Well, I won't say that it is completely useless, but the Linux OS is  available online, for free, from countless mirror servers, so backing up  the OS is not very useful.  One day, when your machine breaks donw and  you have to repair it, you would want to install the latest and greatest  version of Linux, not an old tired backup.  

Over time, you will find that re-installing linux becomes easier and  quick, so I just backup my data and maybe make a tar ball of the /etc  directory.
[/QUOTE]

This may be true but what about the hours (and possibly course of years) in customizations to a setup and also installed programs? I'd assume you can't transport this to a new install? I'm learning here so maybe there is an easy way to do this too? Besides all of that, my internet is very slow so any DL savings helps.

---

### Post by oldfred on 2014-06-23
I backup list of all installed apps to make it easy to reinstall the actual app.
But all your user settings and almost all apps have their data by user in the home folder.

Some server type apps like databases or web servers do have additional folders that are not in /home that should then be backed up separately.

       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
            Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
    
If you manually configure grub, Ethernet, or other hardware or system settings you may also want to backup /etc and other manually configured files. I copy any system file I edit into /home so I just backup /home. And do not automatically restore those files as new system may not need them or need different settings.
 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

---

### Post by buzzingrobot on 2014-06-23
I side with the "Just reinstall, don't clone the OS" argument.  

So... I keep a burned install image on a DVD stashed in the desk. If I break the system so badly that I cannot download a new image, I boot from that. (More than once, I have booted Distro X in live mode, then downloaded and burned a Distro Y ISO to a USB stick.)

I back up my separate /home via rsync cron job. That's primarily to be able to recover files I zap by mistake. If/when I have to restore an installation, I manually partition and don't format /home.

I used to keep a list of installed packages.  These days, I use a post-install script to add my favorite toys.

---

