---
title: "Rookie Question here re: system backup"
date: 2008-04-22
forum: General Help
---

### Post by jlhaslip on 2008-04-22
I've just installed Ubuntu Hardy 8.04 and have a few quick questions to ask of the more experienced people here. These will be terribly "rookie" questions since I am far from experienced in Linux, but have some Unix experience dating back to quite some time ago.

[LIST=1]
[*]System Updates are happening quite frequently. 120 something files the other day and it just updated about 85 files. It took an hour or so to download/install. Will this happen often?
[*]I have managed to instal Hardy 8.04 okay, with a couple of other applications (filezilla, a Lampp, etc), and would like to know how it is possible to do a full system backup to avoid having to re-do all the installation of applications so as to retain all the settings/links, and stuff?
[*]Can I backup the system to CD's as data only? or a bootable CD?
[/LIST]
Incidently, Ubuntu sole boot on the system. Dropped XP completely. 
[http://ohioloco.ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ohioloco.ubuntuforums.org/images/smilies/smiley-faces-75.gif)

Thanks in advance.

---

### Post by jgeezy on 2008-04-22
hello fellow new user!

I have been playing around with Ubuntu for a about a month or so now, currently im running Linux Mint which is basically Ubuntu with a few extra features.  Now, there is a program here called APTonCD that lets you backup all of your programs and instances to a cd or DVD in the menu of Linux Mint.  You might want to look for the same program in your distro, im sure it is there.  As far as an image of your current settings, I don't know how, if there is one i would like to know that as well. it would save me a lot of headache trying to set up the 1390 Broadcom drivers again!  thanks!! Hope this helps a little.

---

### Post by yochaigal on 2008-04-22
Updating is a good thing; and the reason that you're getting so many right now is because of the impending release of Hardy Heron.
There are a few ways to do backups.
For starters, you should move your entire home directory onto it's own separate partition. That way you won't have to format it when you reinstall ubuntu in the future.
See:
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://www.linuxforums.org/forum/redhat-fedora-linux-help/58410-move-home-partition.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/58410-move-home-partition.html)
[http://ubuntuforums.org/showthread.php?t=339795](http://ubuntuforums.org/showthread.php?t=339795)

Now in terms of backup...
SBackup is my favorite.
[http://sbackup.sourceforge.net/HomePage](http://sbackup.sourceforge.net/HomePage)
You can find it in the repositories.

You can make complete partition backups, I'm not sure how you'd make them bootable, though. You could install and run a USB-powered bootable LIVECD of your machine, but I wouldn't recommend it.

---

### Post by jlhaslip on 2008-04-23
Thanks. 

The backup software works well.
I'll simply have to make a note or two about what I have installed and work off that if I have to re-install in the future.

---

