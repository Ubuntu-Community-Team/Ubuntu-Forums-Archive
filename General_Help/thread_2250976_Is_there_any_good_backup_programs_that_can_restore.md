---
title: "Is there any good backup programs that can restore files from a previous day?"
date: 2014-11-01
forum: General Help
---

### Post by nickjanoyan on 2014-11-01
I love Linux distros and like to mess around a lot with them. I like to try to configure stuff and look at tutorials online, but the problem is that a lot of the times I end up messing up my computer. This has happened on so many occasions now. I've looked for free and paid online backup programs to fix the messes I make and none of them worked for me. They either didn't work at all or were extremely slow when trying to back up the files. Basically, all I want to do is back up my entire root folder except the main folders in my home folder (Documents, Downloads, Music, Pictures, and Videos). If I mess up my computer I want to be able to revert to a previous day when I made a backup, but I can't find anything that will let me do that. I was using Deja Dup for a while and it seemed to be perfect. I would backup my files to a server via SSH. Well yesterday I messed up my computer and wanted to restore it, so I went to Deja Dup and did a full restore. I restarted my computer just to be safe. The good news is, it fixed the mess I made, but the bad news is it left all my other new files that I had that day still on my system. As much as I dislike Windows, one feature I liked was their system restore. I just want to restore everything to a previous date and not leave any new files still on my computer. Is there any program that can help me that's like that? This has been driving me nuts, so I could really use some help.

---

### Post by Bucky Ball on 2014-11-01
Clonezilla is your friend. I think all these link are still active.

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

The second one, Create recovery ISO, might be up your alley, but you need to read the first one to create an image first. Just create an ISO of your system partition (or any partition, including Win partitions) and whack it back on when things go pear shaped.

For just regular folder and file backups I use Luckybackup. Dinky name, but real effective and powerful. The first one takes some time, but after that the backup takes no time at all because it only backs up what's been changed. Handy. Which reminds me, better do a backup.

---

### Post by nickjanoyan on 2014-11-01
Thanks. I'll check out Clonezilla and see if it works for me.

---

### Post by Bucky Ball on 2014-11-01
I bought an SSD for my desktop and some more RAM. Cloned the Ubuntu and WinXP partitions from the old IDE drive and cloned them back to the SSD and worked like a charm. You need to do a bit of stuffing around with the stubborn Win bootloader, though, but apart from that ...

If you're just cloning Ubuntu to another partition on another drive it will be a breeze as you can use Boot Repair when you've cloned it back and that will install grub and fix boot in a jiffy. 

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Just make sure the partition you're cloning to is as big as, or bigger than, the partition you've cloned, EVEN IF the OS itself didn't take up all the space in the partition (in other words, you can shrink the partition PRIOR to cloning it to save some space).

---

### Post by nickjanoyan on 2014-11-01
I tried doing what it said in the tutorials, but I kept on running into errors. I appreciate your help, but do you know of anything more user friendly? I'd prefer to have a program I can run on my computer while booted instead of booting off of a disk or USB.

---

### Post by Bucky Ball on 2014-11-01
As I mentioned at the end of my first post: Luckybackup is what I use. 

[QUOTE=BB]For just regular folder and file backups I use Luckybackup. Dinky name, but real effective and powerful. The first back up takes some time, but after that the backup takes no time at all because it only backs up what's been changed. Handy. Which reminds me, better do a backup. [/QUOTE]

---

### Post by nickjanoyan on 2014-11-01
I was just trying that, but I'm having some trouble getting it to upload to a remote server via SSH. I put the source as my documents folder just to test if it works, I clicked the advanced tab, and I put in my server info. Then when I press okay it says I need to specify the destination. I then put an empty folder on my server labeled "/Linux-Backup" and put that as the destination, but it still won't work. Am I doing something wrong?

---

### Post by Bucky Ball on 2014-11-01
Try [THIS]("http://www.ghacks.net/2010/04/13/luckybackup-linux-backup-made-easy/"). 

Down the page a little underneath the heading 'Using Lucky Backup' there is a walkthrough of remote backup. It uses SSH. Do you have that installed? If not, Software Centre or Synaptics and install 'openssh-client'. Installing just  the 'ssh' package may work, but I think that drags in the client and server, which you won't need, I don't think. If this doesn't work, try installing ssh as well.

---

### Post by nickjanoyan on 2014-11-01
I tried the link you posted, but I'm still getting errors. I'm just going to stick with Ubuntu's default backup program. Thank you for your help anyway. I appreciate it.

---

### Post by WinEunuchs2Unix on 2014-11-01
> **Bucky Ball said:**
> Try [THIS]("http://www.ghacks.net/2010/04/13/luckybackup-linux-backup-made-easy/"). 

Down the page a little underneath the heading 'Using Lucky Backup' there is a walkthrough of remote backup. It uses SSH. Do you have that installed? If not, Software Centre or Synaptics and install 'openssh-client'. Installing just  the 'ssh' package may work, but I think that drags in the client and server, which you won't need, I don't think. If this doesn't work, try installing ssh as well.

At the risk of being ex-communicated this Arch Linux link has thorough analysis of backup options: [https://wiki.archlinux.org/index.php/backup_programs](https://wiki.archlinux.org/index.php/backup_programs)

As an aside I'm not sure Aluminum Headgear would protect your brainwaves from Aliens.  Would aluminumn not make it more of antenna?  Would lead-based painted baseball cap be more effective not to mention less conspicuous???

---

### Post by Bucky Ball on 2014-11-01
> **WinEunuchs2Unix said:**
> Would lead-based painted baseball cap be more effective not to mention less conspicuous???

Perhaps, but it wouldn't feel as crinkly.

---

