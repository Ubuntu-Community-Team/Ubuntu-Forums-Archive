---
title: "The art of backing up your system"
date: 2013-03-30
forum: General Help
---

### Post by Nikolai D. on 2013-03-30
Hi all,

a bit of history,

Here we go, finally i want to discuss and learn the right or the different ways of backing up your operating system.
Some years ago i remember that i have learned to use some server 2003 built in backup program to backup and schedule backups of some folders and files. Like for example some shared folders on a windows 2003 file-server. And i think there were even possibilities of doing it like full backups and/or only changes etc. And since then it has kinda stuck in my head that this is one of the right ways to do it. But now after some years, and a view years professionally working in IT (some support / some sysadmining, more client side) i realize that well i actually never used it.

Today,

Now, nowadays, for a view years already i actually use more linux on my workstation('s)/desktops and some servers to. And sometimes i tinker with this systems i use. And since in linux you have very much power at hand you can easily break the system. No matter if it is workstation/desktop or server. I understand that there are alternative methods like using virtualbox or other testing machine for testing. But this is another discussion. This is not always a solution. So what i have learned is to use a CloneZilla Live CD to clone my DualBoot Workstation/Desktops hard disks to an image on an external drive. So i clone it before i know im going to make any major change to the system. So this way cloning whole system disk to an image on an external drive i can always put it back if something goes wrong. And that will be exactly the systems state before i started to make huge changes.

Some explanation,

Why i use a CloneZilla boot disk instead of some build in Windows/Linux program that can backup the system? The point is that sometimes thinkering with the system u can render the system unbootable. And CloneZilla solves this. But the drawback is. If you have multiple Operating Systems on a Computer. And then you also have multiple Computers, this way it is easy to fill up the external storage pretty fast. And as far as i know im not sure i can use any built in backup tool to backup disks comletely because if i render the system unbootable how am i going to put this backups made with a built in program back?

The future or the question itself,

Looking at the things im doing and im trying to achieve, is there any way you can tell me to improve the workflow? I mean i am wondering if there actually is some program that i can use to backup the system and be able to make full backup and then to make kind of incremental backups? Because lets say i have linux on my workstation/desktop now. Im planning to install video drivers. And i dont know if they are goig to break or not. So i make a full system backup. But i already had a full system backup before i installed the video drivers. Because before that i intalled dual boot. And i did a backup of this dual boot. Because have spent time on setting this bual boot to. This way i can always go back to the last working state. And offcourse i delete the some old backups regularly. For example after i installed Outlook 2007 in wine and backed it up also. And everything still works fine. I no longer need the video driver version backup. But if i only added video driver or wine or outlook i dont actually really need to make a whole hard disk backup. Because i added only a view programs to the system. And it would be possible to somehow backup only this additional changes. Not kind of having to backup whole view tens of gigabytes to backup only view tens of megabytes.

Let me know if u can point me to some documentation or any information to learn this,

Thanks in advance,
Nikolai

---

### Post by oldfred on 2013-03-30
What you would use for a business or server should be different than what you might use for a home system as requirements are different. I consider that my home system has little data changing on a daily basis, so I do not do full backups only incremental with rsync and plan a full system reinstall when my hard drive fails.

But everyone has different choices and methods.
       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

I rsync to a backup partition, burn DVDs of the most important data that changes the most,  and know I can restore all the other data if I have to from previous backups or my original CDs (music).

Simple rsync script that I started with:
      
 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

 [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

      Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

 More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

Even more examples of rsync scripts:

 Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

---

