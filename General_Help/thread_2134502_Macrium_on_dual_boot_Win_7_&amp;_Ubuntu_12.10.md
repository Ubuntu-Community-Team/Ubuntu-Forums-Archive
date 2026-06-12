---
title: "Macrium on dual boot Win 7 &amp; Ubuntu 12.10"
date: 2013-04-11
forum: General Help
---

### Post by bruce73 on 2013-04-11
First time Linux user, but with the help of this forum I successfully  set up a dual boot on my Win 7/64 desktop. I haven't done too much yet,  just installed my printer, added Dropbox and configured Thunderbird.  Before I go further and possibly muck things up, I thought it'd be wise  to image the partition. 

I use Macrium on all my Win machines and  swear by it. Is that a good choice for Ubuntu? I googled  a bit and  found a case where the guy had a similar set up, but was unable to boot  from his Windows rescue disc with Linux installed as a dual boot. Has  anyone run into this? 

If Macrium isn't the best solution for  this scenario, what imaging software is recommended (I don't mind paying  for reliability)?

---

### Post by oldfred on 2013-04-12
Users here recommend Macrium for Windows backup.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

But we usually suggest Windows tools for Windows and Linux tools for Linux as then they tend to work better.
With Windows full image backup is a bit more important as it is difficult to reinstall and update. But Ubuntu is easy to reinstall (after a little pratice :) ). So I assume a full new install and just restore my data.
I also have a shared NTFS data partition where I have my Firefox & Thunderbird profiles, so I have the same bookmarks & email in both systems.

      
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Many that do full image use this.

 Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

I prefer rsync and you may want this even if you have a full image as image is outdated the second you do anything.
      
 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

I used the above simple rsync script and modified for my use.

 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by Mark Phelps on 2013-04-12
I've used Macrium Reflect (MR) for backing up Windows for years without any problems, but am a strong believer in using the right tools for the right OSs -- which is why I use Clonezilla for backing up my Linux installs.

---

### Post by weq92f on 2013-04-12
FWIW
I've successfully cloned a Windows 7 dual boot Ubuntu w/grub using clonezilla.  

Hth,

-klb

---

### Post by bruce73 on 2013-04-12
Thanks for all the advice, guys. I'll check out Clonezilla.

---

### Post by The Spectre on 2013-04-12
You might want to give Redo Backup & Recovery a look.
[URL="http://redobackup.org/"]
http://redobackup.org/[/URL]

It has worked great for me.

---

### Post by bruce73 on 2013-04-13
Thanks for the tip.

---

