---
title: "boot/mount issue after dd clone"
date: 2013-08-11
forum: General Help
---

### Post by eric6 on 2013-08-11
Hi, today I ran into some problems while attempting to create a backup solution for my kubuntu system.

I would like my laptop to clone my entire harddrive every night using my internal SSD drive as the source and an external eSATA enclosed drive as the destination.

I succesfully cloned the drive using the command: sudo dd if=/dev/sda of=/dev/sdc bs=4096 conv=notrunc,noerror

However, I have now ran into problems and am not quite sure why. Whenever I reboot my system now (With the eSATA drive still wired up) it boots the OS from the eSATA drive instead of the SSD like it should.  Even when I specifically select the SSD drive from the boot menu, for some reason it boots up Kubuntu that is on the eSATA drive. Additionally, if I unplug the eSATA drive and reboot, it boots the SSD drive as it should. Then when I plug the eSATA wire in and try to access the drive (which should be /dev/sdc like it used to be) from the file browser, Dolphin, I get an error that "according to mtab, /dev/sda5 is already mounted on /; mount failed"

It seems like the issue has something to do with the backup drive taking on the name /dev/sda after being cloned when it should retain its /dev/sdc name?? Is my system confused by both hard drives being /dev/sda ?? Am I not using the 'dd' command correctly? Any help is appreciated, thank you.

---

### Post by oldfred on 2013-08-12
Yes with dd you have made an exact copy & system has duplicate UUIDs. So it does not know which to use or may just not work as it sees duplicates.
A image is just for the case where you do not have it connected when you reboot, but want to have that image.

Better to use rsync or a compressed image. Old fashioned tar, or clonezilla. I use rsync, but do not backup entire system but those things that are different from a standard install. So I can do a new install and then restore my data & customizations. Most user data is just /home. 

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

 Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

      Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

 [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

 Synchronizing UNIX files - Using cp, tar, and rsync
[http://www.ibm.com/developerworks/aix/library/au-filesync/index.html?ca=dgr-lnxw07UNIX-File-Sync&S_TACT=105AGX59&S_CMP=grsitelnxw07](http://www.ibm.com/developerworks/aix/library/au-filesync/index.html?ca=dgr-lnxw07UNIX-File-Sync&S_TACT=105AGX59&S_CMP=grsitelnxw07)

 [https://help.ubuntu.com/community/FileCompression#GNU_Tar_GZ_.28.tar.gz_.tgz.29](https://help.ubuntu.com/community/FileCompression#GNU_Tar_GZ_.28.tar.gz_.tgz.29)

    HowTo: Full backup with tar (older but tar has not changed)
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
/home with tar - matthew
[URL="http://ubuntuforums.org/showthread.php?t=1964130"]http://ubuntuforums.org/showthread.php?t=1964130

[/URL] Oldfred's list of stuff to backup May 2011:
[URL="http://ubuntuforums.org/showthread.php?t=1748541"]http://ubuntuforums.org/showthread.php?t=1748541
      [/URL]
 Some files to exclude from /home backup - post by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

 More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

 
    [URL="http://ubuntuforums.org/showthread.php?t=1748541"]
[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=1964130"]
[/URL]

---

