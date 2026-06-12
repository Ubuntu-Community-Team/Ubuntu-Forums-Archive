---
title: "rm -r Disaster"
date: 2019-04-08
forum: General Help
---

### Post by htrhtrh on 2019-04-08
Hello everybody,
I've just eliminated a folder through rm -r that i shouldn't. I know there is no way to restore it but I would like to know if there is some automatic back up that I can use to restore my file. I'm using ubuntu 16.04.

Best regards

---

### Post by oldfred on 2019-04-08
Short answer No.

This is why we always recommend users have good backups.
       Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)
[URL="https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986"]https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986
      [/URL]
 discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636) 

 If you want to try to recover some data, STOP using system. Only use live installer.
Every bit of use, may be overwriting the data still on drive.
And if SSD trim will houseclean all data.
You will need a lot of time to scan drive, a large drive to copy data to, then lots more time to review & rename files. Photorec finds data on drive, but only by extension, so you have to rename. And it will find deleted copies. I have many copies of same file recovered, but had to then do many compares to see if I could tell which had newest updates since I both added & deleted info.
It took me all night to run photorec. Then several weeks part time to compare all files & reanme, but I had an old backup to also compare to.

      
 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by VMC on 2019-04-08
What folder?

---

### Post by htrhtrh on 2019-04-08
/Desktop/ unfortunately.

---

### Post by deadflowr on 2019-04-08
Was is exactly rm -r /Desktop/?
(You can look at terminal history by simply scrolling up with keyboard arrows)
I ask because there is no such folder called /Desktop.
There is a /home/user/Desktop folder, though. Which can simply be called Desktop.
slashes are important.

Desktop would be the folder that controls anything on the desktop.
Did you have any files on the Desktop?

---

### Post by htrhtrh on 2019-04-08
It's exactly the /home/user/Desktop/ the one I deleted.

---

### Post by raleigh3 on 2019-04-08
If you have deleted home/user/Desktop, then you can recover fairly easy.

It basically contains links to programs that you have/had on your desktop.

I would recreate it.

Then as you add programs to the desktop, it will repopulate itself.

---

### Post by khwarizmi on 2019-04-08
In the future, consider installing and using trash-cli. It allows you to use the same functionality as the GUI trash can but on the command line. Accordingly, items deleted accidentally can be restored from the trash.

---

