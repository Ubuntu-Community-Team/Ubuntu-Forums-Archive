---
title: "dual boot - already have ubuntu need xp"
date: 2006-08-14
forum: General Help
---

### Post by mccarthy on 2006-08-14
Sadly, I can't get wine working with most games, and in order to play I must dual boot with XP.  How do I install XP on my computer without formatting my entire disk?  I have empty space (about 13GB) set aside for XP at the end of my HD, my CDROM is first in boot priority, the disk is recognized in Ubuntu (its not scratched), and it is in the drive. Reboot, and Ubuntu starts to boot from the HD!  From what I could tell from a quick Google search I might need to make boot floppies?  With a program called WinXP_EN_HOM_BF.EXE?  Please help.  I don't understand how Ubuntu's installation was so easy (put in disk, boot, presto desktop! - install and surf the web) when it is free software, while Windows gets paid out the *** to do the same thing and it magically doesn't work...lame.

I like how windows has become a gaming platform for me, like nintendo.

---

### Post by ciscosurfer on 2006-08-14
In general, Windows likes to be installed first.  This is due to issues involving its MBR.  Below are some links that you will find useful.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by mccarthy on 2006-08-14
Thanks for the links.  I looked through them but they all seem to be focused on getting Ubuntu on a Windows system, as opposed to putting Windows on an Ubuntu system which is what I'm doing.  Does anyone know if it would be possible to move my linux partition to the end of the HD without losing the information?  Would that allow me to boot to the Windows disk?

---

### Post by Tomosaur on 2006-08-14
I think what cisco meant was that you can't install XP without temporarily losing access to Ubuntu. You will need to install XP, then reinstall Grub, to get access to linux back.

---

### Post by mccarthy on 2006-08-14
Ohhh...thanks.  It's true that you have to install xp first or else jump through hoops, so I've decided to make a backup of my / based off a howto I saw ([http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087) - yes i know its for 5.04 but the process doesn't seem to be version-dependent).  I'll put it on another hd and then I'll wipe my hd and install xp first, then copy my backup to my new Ubuntu partition and hope it works.  I'm guessing I'll have to mess around on a live cd to get it to work, and those links will probably come in handy to get grub working.

If only developers would make games for linux, I would never have to look at windows again.  Speaking of which, I was wondering what modern linux games you guys are playing?

---

### Post by MarinaraOfDeath on 2006-08-14
*Quick (and safest) answer*
Install XP first.

*More useful (but riskier) answer*
[LIST]
[*]Use qtparted or gparted to create a windows partition (which, as I recall reading in a thread somewhere round here, is the biggest problem since ext3 isn't necessarily the best at behaving after being resized).
[*]When done repartitioning but before quitting the partition editing program, set the newly created partition as the primary partition AND hide the other partitions.
[*]Install windows
[*]Reinstall grub
[/LIST]
This can get it done, but is also might hose your linux install, so it's up to you to decide.

---

