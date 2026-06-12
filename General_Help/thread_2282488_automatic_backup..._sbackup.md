---
title: "automatic backup... sbackup??"
date: 2015-06-14
forum: General Help
---

### Post by Old Jimma on 2015-06-14
Hi Community:

I bought an WD My Cloud for the purposes of providing further insurance that I have a viable backup to my data.

Currently, I'm running a shell script that copies my home directory to the WD My Cloud (incredibly slow > 6 hours!)

I decided to investigate doing incremental backups with sbackup.



However, I was very concerned when
[LIST]
[*]I read a wiki that says sbackup currently has 48 unresolved bugs ([https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") and [https://bugs.launchpad.net/sbackup]("https://bugs.launchpad.net/sbackup")),
[*]and found many complaints on the forums about sbackup not restoring files. 
[*]
[/LIST]

It was pretty disturbing to learn that I could place my faith in sbackup and have it fail in my time of need because of bugs!! :-(

IN fairness to sbackup the wiki was 6 years old, and perhaps it has made progress since then, but I didn't find any thing that said sbackup was really reliable since the 2011 wiki.

Could somebody provide guidance on an automatic backup/restore software that is reliable??

Thank you!
Old Jimma

---

### Post by TheFu on 2015-06-15
I've been using rdiff-backup for about 6 yrs to backup 20-30 systems. Never had issues restoring.
However, the backup storage needs to be a UNIX file system with linux permissions, linux owners, linux groups, linux ACL support, **not NTFS**. That will be a requirement for many of the solutions which have the least risks.

Until a bare metal restore is actually performed, there is no certainty that any backup is actually working in the way needed or expected.  My signature has more links about backups and I've seen some other active members here with great tips on good backup tools - search a little to find those posts.

I should say that I DO NOT backup everything on a system. Instead, I backup settings, lists of installed packages and data so the system can be restored to the same point it was.  That saves about 4-8G of backup storage per system, which means another 30 days of daily backups can be retained.

rdiff-backup isn't perfect and it isn't for everyone. Also, I've never looked at sbackup.

---

### Post by Old Jimma on 2015-06-15
Hi The Fu:

Thanks for your reply (and replies on my previous posts). I appreciate it.

Currently, I have a 2nd HD in  my computer and use crontab to run a shell script to back up my primary HD to it every week. Also, I have an external HD that I use to back up my system once a month. 

About 2 weeks ago, the SATA cable to my DVD caught fire where it joins to the DVD, and I freaked out... and decided that I should have a back up that is outside of my computer's box.

I thought I could use the WD My Cloud for further redundancy of backing things up... 

However, I really dislike it because it is so incredibly slow (it took 10 hours to back up my system yesterday), and doesn't work with Ubuntu all that well, or at least, I will have to struggle more to make it work with Ubuntu reasonably well.

What would have been your idea of a good NAS for an Ubuntu home user to do nothing more than to back up a system that has a 64GB SSD for the operating system, and a 1Tb drive for the /home partition?

Maybe I'll sell the WD on Ebay or Craigslist. I don't like it very much.

Thanks,
Old Jimma

---

### Post by nerdtron on 2015-06-15
It's always good to have a backup plan. And here's a like for good NAS [http://lifehacker.com/5968677/five-best-nas-enclosures](http://lifehacker.com/5968677/five-best-nas-enclosures)

Should you buy a NAS or build your own? [http://lifehacker.com/should-i-use-a-diy-pc-for-my-nas-or-buy-an-enclosure-1678991505](http://lifehacker.com/should-i-use-a-diy-pc-for-my-nas-or-buy-an-enclosure-1678991505)
And here's how to setup your own just in case: [http://lifehacker.com/turn-an-old-pc-into-a-nas-vpn-media-streamer-and-mor-1516484110](http://lifehacker.com/turn-an-old-pc-into-a-nas-vpn-media-streamer-and-mor-1516484110)

---

### Post by sudodus on 2015-06-15
If backup to USB is slow, it is probably USB 2. In an old computer eSATA and in a new computer USB 3 might be good alternatives, that are much faster (than USB 2). But it is a good idea to use an incremental method, and I would rely more on TheFu's suggestion, rdiff, than on sbackup.

But test (with a third HDD), that it really does what you want, that you can restore a working system :-)

---

### Post by TheFu on 2015-06-15
> **sudodus said:**
> If backup to USB is slow, it is probably USB 2. In an old computer eSATA and in a new computer USB 3 might be good alternatives, that are much faster (than USB 2). But it is a good idea to use an incremental method, and I would rely more on TheFu's suggestion, rdiff, than on sbackup.

But test (with a third HDD), that it really does what you want, that you can restore a working system :-)

10-base-tx and USB2 disks are too slow for large backups.
GigE and/or USB3 are great for backup targets.  eSATA is even better, because you can run an OS off it and not run into queuing issues that happen when an OS is running 50 different processes. USB has issues when there are too many conflicting requests - IME.

I do have a 2TB WD USB3 external disk that has been used for backup storage.

I cannot recommend any NAS devices - don't use them. Sorry.  Always build my own, which are currently running Ubuntu Server. rdiff-backup works over ssh - so "sharing storage" isn't needed/desired for the backups to work. Client machines cannot harm the backup storage on another machine without greater knowledge about the backup tool and method used. The backup storage area isn't "mounted" to the clients.

And just for clarity - rdiff-backup is NOT "rdiff" - those are 2 different things.  Last week or the week before, I remember someone else suggesting a different backup tool and did a little research about it - it was a way to make a bootable, installable Ubuntu with all your programs based on an existing installation. It wasn't a mirror and didn't do incrementals, but having 1 "image-based" backup could be smart for many people. Didn't try it myself - I'm easily distracted - but it does sound interesting for people who aren't as advanced to know exactly what they need to get their system restored from a less-than 100% backup solution.

Lots of options are available, depending on your needs and skillz. That can be confusing AND extremely flexible.

---

### Post by pfeiffep on 2015-06-15
> **Old Jimma said:**
> Hi Community:

I bought an WD My Cloud for the purposes of providing further insurance that I have a viable backup to my data.

Currently, I'm running a shell script that copies my home directory to the WD My Cloud (incredibly slow > 6 hours!)

I decided to investigate doing incremental backups with sbackup.



However, I was very concerned when
[LIST]
[*]I read a wiki that says sbackup currently has 48 unresolved bugs ([https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite) and [https://bugs.launchpad.net/sbackup](https://bugs.launchpad.net/sbackup)), 
[*]and found many complaints on the forums about sbackup not restoring files. 
[/LIST]

It was pretty disturbing to learn that I could place my faith in sbackup and have it fail in my time of need because of bugs!! :-(

IN fairness to sbackup the wiki was 6 years old, and perhaps it has made progress since then, but I didn't find any thing that said sbackup was really reliable since the 2011 wiki.

Could somebody provide guidance on an automatic backup/restore software that is reliable??

Thank you!
Old JimmaI also have a WD My Cloud and found that using the built into Ubuntu Backup program works perfectly with My Cloud. Since I wanted to insure I had My Cloud backed up I also have a WD My Book Studio connected to the My Cloud USB3 port. I saw no need to backup my Ununtu backup using the My CLoud Safepoint so I targeted My Book Studio for Ubuntu.

---

### Post by RobGoss on 2015-06-15
Hello and welcome, It seems as tho something is wrong when you create your backup. I would never wait 6-hours for any backup I'm very funny like that. I'm fairly new to Ubuntu and I also like to keep things safe especially my OS system. Try Clonezilla it works great and very fast [http://clonezilla.org/](http://clonezilla.org/)

---

