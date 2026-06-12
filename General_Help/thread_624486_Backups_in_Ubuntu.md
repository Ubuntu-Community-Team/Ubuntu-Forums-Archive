---
title: "Backups in Ubuntu"
date: 2007-11-27
forum: General Help
---

### Post by ZachSka87 on 2007-11-27
I'm a curious person and I like to push the envelope a lot, especially in linux.  As such, I frequently ruin perfectly good installations and have to redo them, including replacing all of my settings, customizations, etc.

Is there a way to backup my machine, or at least my Ubuntu install, into something of an image similar to GHOST so if I mess it up I can just pop a disk in and not have to reconfigure everything the way I like it?

---

### Post by Xavieran on 2007-11-27
Try this one:[Remastersys]("http://linux.softpedia.com/get/Utilities/Remastersys-26479.shtml#")...
apparently it backs up *Everything* including software.

---

### Post by ZachSka87 on 2007-11-27
Looks interesting...

I see that it creates a LiveCD...but can I then reinstall that on my machine?

---

### Post by erginemr on 2007-11-27
> **ZachSka87 said:**
> I'm a curious person and I like to push the envelope a lot, especially in linux.  As such, I frequently ruin perfectly good installations and have to redo them, including replacing all of my settings, customizations, etc.

Is there a way to backup my machine, or at least my Ubuntu install, into something of an image similar to GHOST so if I mess it up I can just pop a disk in and not have to reconfigure everything the way I like it?

Hello,

Same as I, who also like messing up with the Linux system and have to restore it sometimes.

For this purpose, I am using the following method:

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

to backup my entire system at regular intervals. This method is straightforward and fail-safe, but will take a few hours to backup the complete system. You can then keep the newly formed single, compressed file in a backup folder or burn it to a CD / DVD. when the time comes for restore (it eventually will for geeks), you can run a Live CD and restore your system byte per byte using this backup file.

You may also refer to the following Ubuntu help page that discusses alternative ways to backing up:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

