---
title: "Backup for a dual boot."
date: 2007-08-03
forum: General Help
---

### Post by eugman on 2007-08-03
I have an external harddrive and a dual-boot laptop with widnows and ubuntu. I want to back up the important data or more specifically the "home" folders of each OS. Something that can exclude specific folders. Even better if it can backup incrementally.

---

### Post by apetresc on 2007-08-03
I don't think there exists a single backup method that will transparently work on both Windows and Linux. The best you can do is mount your Windows drive, create some symbolic links in a directory on your Linux drive that point to the directories on the Windows drive that you want to have backed up, and then use a Linux-only backup solution. There are plenty of those. Check out the following links:

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)
[http://hddsaver.com/content/26/](http://hddsaver.com/content/26/)

If you need something more, let us know :)

---

### Post by djroze on 2007-08-20
Hey there,

   I also have been wondering about a dual boot backup solution; I just reinstalled Windows XP and put Feisty Fawn on in lieu of my previous LFS installation.  Ideally, I'd like to backup both my personal files and system stuff too, scheduled, with a GUI, and I figure it's also the case that I only need to worry about backing up Linux files when logged in to Linux, and likewise with Windows.  That is, supposing for some reason I don't use Windows for two weeks, I have no need to perform additional backups of its data anyway.  I'd like to understand a little better what the options are, and I remember looking around a while ago for a free Java backup program (i.e. cross-platform).  Anyway, I'm also a software developer, so if there is enough interest, I'd consider starting an Open Source project or something for a Java backup program.

- DJ

---

### Post by logos34 on 2007-08-20
djroze, 

**Sbackup** might be an option for you.
[http://sourceforge.net/projects/sbackup/](http://sourceforge.net/projects/sbackup/)

**sudo apt-get install sbackup**

---

### Post by djroze on 2007-08-20
Hi logos,

   Thanks for the suggestion, but SBackup doesn't support Windows, does it?

- DJ

---

### Post by logos34 on 2007-08-20
> **djroze said:**
> Hi logos,

   Thanks for the suggestion, but SBackup doesn't support Windows, does it?

- DJ

no, but you could backup the files on your (mounted) windows partitions using Sbackup from the linux side. To restore (i.e. write)  to NTFS partitions you'd only need to be using the  ntfs-3g driver. But I haven't personally tried that.

here's a link to their website (looks like a work in progress!):
[http://sbackup.sourceforge.net/RestoringFiles](http://sbackup.sourceforge.net/RestoringFiles)

---

### Post by djroze on 2007-08-20
Hmm, interesting...I guess that could work, although I know that I often tend to be somewhat idealistic about Linux in that I install it hoping to use it a lot, but it ends up collecting dust while I use XP (awful, I know ;).  I think it'd be kind of neat to be able to configure a single backup profile that was accessible from a cross-platform client running as a service, so that there's no worry about necessarily being logged in to one or the other.  To give an example of my usage scenario, I'd really like to be able to do whatever on either Linux or Windows and know that when I leave my computer on and go to sleep at night, my documents and other stuff will be backed up (regardless of what OS is running).

And since I have a shared FAT32 partition, I could see such a program providing two components for the backups: platform-independent backups (such as everything in my shared documents folder, which will be backed up regardless of what OS is running), and an OS-specific backup.  The OS-specific backup could specify files such as certain Linux directories, or even launch the user's favorite platform-dependent backup utility to perform the necessary operations!  Does that make sense, and am I the only one who would really bother with this?  :)

- Daniel

---

### Post by logos34 on 2007-08-20
If it's fat32 then that makes things a bit easier.

I use a separate backup program for winxp side.  There may be a cross-platform backup program that would meet your criteria, just not aware of it.  

You could try to run a windows backup application in linux using Wine, but not everything works under wine as it should.

---

### Post by djroze on 2007-08-20
OK, thanks.  I'd probably not wanna trust my backups to WINE, but if anyone else can provide info about cross-platform backup solutions that might work for this, I'd love to hear it.  Also, if enough folks would be interested in a program like this if it doesn't exist, I might be keen to write it myself like I mentioned above.

---

### Post by capink on 2007-08-24
rsycn can do incremental backups in linux. As for windows, I would think that rsync might be available under Cygwin, but I'm not sure.

---

