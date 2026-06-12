---
title: "Raid is my new friend. But what about if I lost the main drive?"
date: 2022-06-13
forum: General Help
---

### Post by josephchrzempiec on 2022-06-13
Hello, I'm working on a server but just using the ubuntu Desktop latest OS. I was wondering something. Sense I have a 120GB SSD as my main drive and two 1TB drives in a Raid one for redundancy and I don't use much space. I was wondering what happens If i lose the main drive and Put on a new hard drive and reinstall the OS. How can I recover the Raid without losing it all?

The other question is If the main drive fails for any reason can I pull one of the redundant drives out and put it into my other linux system so I can still access the files? Any information would be great Thank you.

Joseph

---

### Post by oldfred on 2022-06-13
RAID is not backup, it is for uptime or availability on a server.
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

Depends on what type of RAID.
If RAID 0 half of data is on one drive & half on the other. 
If FakeRAID, or vendor RAID card, you need same hardware.
Often better to use Linux software RAID, mdadm, if using RAID.

Disk setup, Partitioning, Mounting, Adding - Where to begin ? 
[https://ubuntuforums.org/showthread.php?t=2459660&p=14027975#post14027975](https://ubuntuforums.org/showthread.php?t=2459660&p=14027975#post14027975)
[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)
[https://ubuntuforums.org/showthread.php?t=2470818](https://ubuntuforums.org/showthread.php?t=2470818)

[https://askubuntu.com/questions/1234949/install-ubuntu-20-04-focal-fossa-with-raid-1-on-two-devices](https://askubuntu.com/questions/1234949/install-ubuntu-20-04-focal-fossa-with-raid-1-on-two-devices)

---

### Post by josephchrzempiec on 2022-06-13
Hello, I had to change that I keep forgetting about the raid is not a backup. I'm on a Raid 1 setup. The system I have doesn't have a hardware raid and I do not have any raid cards. This is a software raid. At the moment this is all I can do. Lack of funds made that happen. 

Joseph

---

### Post by TheFu on 2022-06-14
Backups first. 
RAID 1 second.

Backups are 1000x more important than RAID.  If you only have 1 choice, do backups.

RAID solves 2 issues.
* High-availability
* Read performance
Nothing else.  It isn't for preventing data corruption or data loss. That's what automatic, daily, versioned, backups do.  There's no comparison.

If you don't want to lose settings and data, setup backups.

Did I beat this topic into submission enough?

---

