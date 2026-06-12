---
title: "Ubuntu as Backup Server"
date: 2006-12-01
forum: General Help
---

### Post by Banagor on 2006-12-01
Hey all,

Really quick question that perhaps somebody can help me with. :)

I've just set up an Ubuntu server at a client's office as a backup server. It can see the Windows XP shared folders from which they work all day. What I need to know is how to automatically backup those folders to the Ubuntu server every night as some sort of automated process.

Any ideas? And yeah, I'd rather they were on Ubuntu for both those servers, but they wouldn't have a clue and I don't want to...frighten them (although, btw, kudos to Ubuntu designers as they love the glossy desktop look and feel - as do I).

Thanks for any info! :) I just need something really simple and easy to do this around 9pm every night or something.

---

### Post by koenn on 2006-12-01
you could use a command such as 'smbget' to copy from the Windows shares into a directory on the ubuntu server. 
The schedule it, you can create a cron job.

you can do 
man smbget
man chron

to get the exact syntax you need. You may also find some help on chron on the www. (Don't know the syntax by heart and i'm not in the mood to go look it up)

rsync is also a great tool for disk-to-disk backups because it only transfers changes in files, not complete files. There's an rsync for Windows as well, but I don't know if you can get it to work between a Linux and a Windows system. 
If it works, you might be able to backup folders that aren't shared so it's worth a look.

---

### Post by technodigifreak on 2006-12-01
I agree, rsync/unison are great tools

I think that SBackup would be a better solution though, especially if you are archiving as well (and you should be!)  

Debian Admin as a great article on installing and using SBackup on an Ubuntu System

[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

Just mount the windows shares and SBackup should be able to take care of the rest.

---

### Post by Banagor on 2006-12-01
Ah! Thanks!

Very much appreciated. I'll check it out right now. I can probably do an apt-get on those or something, I imagine?

---

### Post by technodigifreak on 2006-12-01
I believe that SBackup is in the main repositories (if memory serves), a simple search in Synaptic should bring it up, if not you may need to enable the universe or multiverse repositories.

The Debian Admin article is very verbose and should walk you through the entire process.

Also, you may want to edit your fstab file to automount the windows shares when the Ubuntu server boots (just in case).

Another thought is that you may want to use systemimager once a month or so on the windows server to have a (quick) full restoration and then you can use your backups to bring it up to date. - anyway, just a thought.

***edit**
as an afterthought, an option for the windows desktops would be to simply share out the "backup" drive on the Ubuntu server and use 'ntbackup.exe' that's included in XP Pro (but can be copied to an XP Home machine and run the same) to run backups on the clients every night to the shared drive.  Then end result will be about the same but may alleviate issues if people sometimes forget to leave their computer's on......

the advantage of the first option (SBackup) is central admin, and you can use clamav to scan the XP machine's shared drives before/after a backup is run, giving you more value added :D

---

