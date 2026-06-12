---
title: "System Restore For Linux (Time Shift Or Other Option?)"
date: 2015-05-14
forum: General Help
---

### Post by younglemon on 2015-05-14
Why isn't there an OS file restoration program readily available within Ubuntu?  
Although I've never needed it, I was hoping to have it if I ever did.  I looked around the forums and in the Ubuntu help and there weren't any posts that had System Restore in the title.  I just went to the post ['things you don't like about Ubuntu']("http://ubuntuforums.org/showthread.php?t=797223") and posed this question and thankfully someone replied with the two suggestions, try [Time Shift]("http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html") and make a new thread so that it can be found.  

I have excerpted the following from the page located here: [http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html](http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html)

Thank you to Ubuntu Geek for the following information.  I haven't tried it yet, but it seems that this is the way to enable 'System Restore' functionality within Ubuntu.  I just hope with works with the my version of Ubuntu 14.04lts.  When I try it, I'll reply/comment here.

-----------------------------------------------

"TimeShift for Linux is a application that provides functionality similar to the [[COLOR=#009900]_System Restore_[/COLOR][IMG]http://images.intellitxt.com/ast/adTypes/icon1.png[/IMG]]("http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html#") feature in Windows and the Time Machine tool in Mac OS. TimeShift protects your system by taking incremental snapshots of the file system at regular intervals. These snapshots can be restored later to bring your system to the exact state it was in at the time when the snapshot was taken.

 Snapshots are taken using rsync and hard-links. Common files are shared between snapshots which saves disk space. Each snapshot is a full [[COLOR=#009900]_system backup_[/COLOR][IMG]http://images.intellitxt.com/ast/adTypes/icon1.png[/IMG]]("http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html#") that can be browsed with a file manager.**Features:**
**Minimal Setup**
 TimeShift requires very little setup. Just install it, run it for the first time and take the first snapshot. A cron job will be enabled for taking automatic snapshots of the system at regular intervals. The [[COLOR=#009900]_backup_[/COLOR][IMG]http://images.intellitxt.com/ast/adTypes/icon1.png[/IMG]]("http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html#") levels can be selected from the Settings dialog.
 Snapshots are saved by default on the system (root) partition in path /timeshift. Other linux partitions can also be selected.
**Boot Snapshots**
 Boot snapshots provide an additional level of backup and are taken 30 minutes after the system is started.
 Hourly, daily, weekly and monthly levels can be enabled if required.
**Better Snapshots and Rotation**
 TimeShift runs at regular 30-minute intervals but takes snapshots only when needed.
 Applications like rsnapshot rotate a snapshot to the next level by creating a hard-linked copy. Creating a hard-linked copy may seem like a good idea but [[COLOR=#009900]_it_[/COLOR][IMG]http://images.intellitxt.com/ast/adTypes/icon1.png[/IMG]]("http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html#") is still a waste of disk space. This is because only files can be hard-linked and not directories. The duplicated directory structure can take up as much as 100 MB of space. TimeShift avoids this wastage by using tags for maintaining backup levels. Each snapshot will have only one copy on disk and is tagged as "daily", "monthly", etc. The snapshot location will have a set of folders for each backup level ("Monthly", "Daily", etc) with symbolic links pointing to the actual snapshots tagged with the level.
**System Restore**
Snapshots can be restored either from the running system or from a live CD. Restoring backups from the running system requires a reboot to complete the [[COLOR=#009900]_restore_[/COLOR][IMG]http://images.intellitxt.com/ast/adTypes/icon1.png[/IMG]]("http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html#") process.
**Cross-Distribution Restore**
You can also TimeShift across distributions. Let's say you are currently using Xubuntu and decide to try out Linux Mint. You install Linux Mint on your system and try it out for a week before deciding to go back to Xubuntu. Using TimeShift you can simply restore the last week's snapshot to get your Xubuntu system back. TimeShift will take care of things like reinstalling the bootloader and other details. Since installing a new linux distribution also formats your root partition you need to save your snapshots on a separate linux partition for this to [[COLOR=#009900]_work_[/COLOR][IMG]http://images.intellitxt.com/ast/adTypes/icon1.png[/IMG]]("http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html#").
**Excluded Files**
TimeShift is designed to protect system files and settings. User data such as [[COLOR=#009900]_documents_[/COLOR][IMG]http://images.intellitxt.com/ast/adTypes/icon1.png[/IMG]]("http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html#"), pictures and music are excluded by default. This has two advantages:
 You don't need to worry about your documents getting overwritten when you restore a previous snapshot.
 Your music and [[COLOR=#009900]_video_[/COLOR][IMG]http://images.intellitxt.com/ast/adTypes/icon1.png[/IMG]]("http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html#") collection will not waste space on the backup device.
**Install timeshift in ubuntu 13.10/13.04/12.10**
Open the terminal and run the following commands
[INDENT]sudo apt-add-repository -y ppa:teejee2008/ppa
 sudo aptitude update
 sudo aptitude install timeshift
[/INDENT]-----------------------------------------------------------------

---

### Post by monkeybrain20122 on 2015-05-14
Well I have a very simple solution. I have a separate /home partition which stores all the data and doesn't require system restoration (backing up files in any way is sufficient) The system lives in a small / partition about 13 G. I use fsarchiver to clone the / partition once a few days or before I have an update which i fear may break something (I use bleeding edge graphic driver from ppa) It takes about 10 minutes during which I can use my computer (except not to run updates or installation which would confuse the imaging obviously) If something goes wrong I just restore the image. Takes less than 5 minutes. [http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)
The catch is it probably doesn't work with the uefi gpt kind of setup (though according to the rescue CD homage it does work for gpt [http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage))

Edited: I think this is a better solution than complicated system restore options because it is fast and clean and you can be 100% sure that the system is restored to the previous state (reformat / partition before restore) so it is not like some kind of programs that use complicated calculation to track history and so on, which is always problematic because complicated things are more likely to go wrong(e.g Windows' system restore is just an approximation of what the system was and not very reliable according more experienced people on this forum)

---

### Post by tea for one on 2015-05-14
Good evening

Here is another suggestion:-

Systemback

[https://launchpad.net/systemback](https://launchpad.net/systemback)

[http://www.unixmen.com/systemback-restore-linux-system-previous-state/](http://www.unixmen.com/systemback-restore-linux-system-previous-state/)

Kind regards

---

### Post by younglemon on 2015-05-14
Hey thanks so much for replying.  Is Systemback the solution you employ?  Have you ever used Time Shift?  I wish there was one that was a part of Ubuntu and came out-of-the-box, if you will.

---

### Post by younglemon on 2015-05-14
So are you backing up the Ubuntu OS system files or your /home files with this solution?  I know you're not supposed to be grateful and thank anyone, but I am so, thank you for replying.

---

### Post by tea for one on 2015-05-15
> **younglemon said:**
> Hey thanks so much for replying.  Is Systemback the solution you employ?  Have you ever used Time Shift?  I wish there was one that was a part of Ubuntu and came out-of-the-box, if you will.

Luckily, I've never had to use Systemback in an emergency because Ubuntu is pretty solid. 

I have used it to test if it does what it says on the tin. I have successfully created a system image, converted it into an ISO, popped it onto a USB stick and installed it on an external hard drive. 

I have not used Timeshift.

---

### Post by tea for one on 2015-05-15
> **younglemon said:**
> So are you backing up the Ubuntu OS system files or your /home files with this solution?  I know you're not supposed to be grateful and thank anyone, but I am so, thank you for replying.

I do not know where you got the impression that you should not be grateful for useful replies. 

I'm sure that many forum users are happy to share their knowledge/experience and an expression of gratitude can only encourage people to post their solutions more frequently.

Marking threads as "solved" should also be positively supported.

Anyway, back to topic, other users have also recommended Clonezilla and Redo Backup as alternative system image applications.

Good luck with your endeavours and let us know which application has proved suitable for you.

---

### Post by Mark Phelps on 2015-05-15
You need to understand that "system restore" (from Windows) does NOT do what the name implies -- restore the entire working PC.  Instead, what it does is make backups of all system files and settings replaced during Windows Updates.  Then later, when you do a System Restore, all it does is overwrite the current system files and settings with the backups saved earlier.  So basically, it should be renamed Operating System Restore.

A much better solution, one that many of us use, is to periodically image off the OS and its contents.  This way, you can actually restore the entire setup in only a few minutes.  Apps like Clonezilla and RedoBackup ofter this feature.

---

### Post by leunam12 on 2015-05-15
Another good idea is to learn to use rsync.

I regularly rsync my home folder and my storage drive to a removable HDD. I also create images of my / and home partitions on a regular basis using clonezilla. Clonezilla is a pretty reliable system to keep backup of your system that can be restored easily if there are problems or if an update breaks the system. It has the inconvenience that it has to booted from USB or DVD and it cannot do incremental backups but it has saved me quite a few times when one of my crazy experiments went bad and I had to go back to square one or when I tried to install a package from source and it broke the system.

I have used RedoBackup once but I had a couple of problems with it: first: it would not boot unless I disabled fastboot and enabled legacy boot on the BIOS; and second: I could not get it to save the image on a specific folder in my backup drive, rather it saved in the HDD's root. Also I didn't see any options for dragging and dropping.

---

### Post by younglemon on 2015-05-15
You all are really very awesome and have provided me with some great alternatives to further research.  Although I haven't continued on with this yet, I'm going to reread all the comments and suggestions and then decide which one I'm going to attempt first.  Thank you to all of you that replied, I'm sure that one of these suggestions will work nicely.  I will mark this as solved for now and reply back with my results.

---

### Post by Download_Descenden on 2016-04-30
Have to say, I have found Timeshift excellent software.

[COLOR=#000000]I've used it on Lubntu and Linux Mint and it's never failed me yet. 

 It's saved me a few times when installing unfamiliar software and making changes etc, and after having some issues with 16.04 been using it etc.[/COLOR]

[COLOR=#000000]Details and ppa here. [/COLOR]

[http://www.teejeetech.in/p/timeshift.html](http://www.teejeetech.in/p/timeshift.html)

---

