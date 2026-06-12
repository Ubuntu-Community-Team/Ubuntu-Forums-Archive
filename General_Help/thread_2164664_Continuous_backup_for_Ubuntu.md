---
title: "Continuous backup for Ubuntu?"
date: 2013-08-01
forum: General Help
---

### Post by woodyg on 2013-08-01
Hi,
I am looking for a tool that can perform continuous, unencrypted, backups of the files on my main laptop and put those on my secondary computer. Up until now I have been using scheduled backups with LuckyBackup, but I really should find a tool that can do continuous backups. I am already using CrashPlan for encrypted backups to the cloud, but I would also like an unencrypted local backup. I found [a long list of backup tools]("https://en.wikipedia.org/wiki/List_of_backup_software"), many which were available on Linux, but I would like to know which ones you recommend before going ahead. I am using ubuntu 12.04.

---

### Post by dino99 on 2013-08-01
This is the default ubuntu tool : [http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/](http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/)

---

### Post by slickymaster on 2013-08-01
> **9d9 said:**
> This is the default ubuntu tool : [http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/](http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/)

+1 on Déjà Dup.

Anyway, if you're in doubt of which one to use you can read this comparative between several options: [Comparison of backup tools]("http://askubuntu.com/questions/2596/comparison-of-backup-tools")

---

### Post by woodyg on 2013-08-01
> **9d9 said:**
> This is the default ubuntu tool : [http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/](http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/)

It thought Deja Dup didn't offer continuous backup, does it?

---

### Post by slickymaster on 2013-08-01
> **woodyg said:**
> It thought Deja Dup didn't offer continuous backup, does it?

Déjà Dup offers incremental backups, letting you restore from any particular backup.

---

### Post by woodyg on 2013-08-01
> **slickymaster said:**
> Déjà Dup offers incremental backups, letting you restore from any particular backup.

But is it continuous?

---

### Post by sudodus on 2013-08-01
Maybe RAID would solve your problem

[https://en.wikipedia.org/wiki/RAID#RAID_1](https://en.wikipedia.org/wiki/RAID#RAID_1)

---

### Post by slickymaster on 2013-08-01
> **woodyg said:**
> But is it continuous?

If you're referring to a permanent and continuous process, no, in that sense it isn't. What it does is that after the first backup, the program only send changes to the server or external drive, USB flash drive, whatever has been chosen as repository for the backups.

---

### Post by dino99 on 2013-08-01
As said above, RAID is the "continues" process per se; but deja-dup can also be used via a cronjob, where you set it as you need.
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by ken3 on 2013-08-01
First, let me say I don't know of a continuous backup solution for Linux.

Second, let me apologize in advance if this sounds preachy.  I disagree with the premise of continuous backups for anything except mission critical applications, meaning you stand to lose your entire business or even a few human lives if something breaks.  But that's my opinion, and you obviously disagree.

Is there a reason why a highly frequent (near-continous) backup wouldn't work?  Or better yet, a nightly backup?

My normal solution would be RAID, but since you're on a laptop you probably don't have room for two internal disks.

Continuous backups have some serious disadvantages IMO:
[LIST=1]
[*]They're a pain to set up.
[*]They take a lot of resources compared to other solutions, unless they're baked into the OS (hooked into the disk driver the way RAID is).
[*]You're stuck with your data in a format that probably needs a specific tool to get it back.
[/LIST]

I've set up a bunch of different backup schemes since the 80s, including tape backups back in the day.  Most of those schemes I never had to restore from, and some of them that I did turned out to be non-workable solutions, meaning that I couldn't restore a single backup in the entire collection.  The last tape backup I ever used was one of the nonworking ones, and it's the first time I actually needed the backup.  I suspect none of the tape solutions would actually have worked.

I personally back my data up by a recursive copy to another device, into a folder whose name is a date stamp.  If the data is critical, that device will be across a network of some sort, or to a removable SATA drive so I can swap it out.  I don't do incremental backups, and I don't compress anything.  If I need room for the backup, then I delete the oldest from my disk.  I don't back up the entire computer, just the data I care about.

When you get a failure, it never happens at a convenient moment.  You need the data, you need it immediately and you don't have time to read a manual.

I know this is not flashy or convenient, but the real convenience of a backup solution comes when you need your data back after a failure.  It doesn't require anything special, just some computer with support for that filesystem.

The more complicated a backup solution is, the more likely it is to fail.  Speaking from experience, you will never know about the failure until you need the backup.

---

### Post by slickymaster on 2013-08-01
> **9d9 said:**
> As said above, RAID is the "continues" process per se; but deja-dup can also be used via a cronjob, where you set it as you need.
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Not quite. Referring to [https://wiki.gnome.org/DejaDup/HowItWorks](https://wiki.gnome.org/DejaDup/HowItWorks):
> **Scheduling**
Déjà Dup does not use cron or similar schedulers. Rather, it starts a program deja-dup-monitor when you log into your session. This keeps track of when you last successfully backed up and will wait until the next scheduled backup.
It determines exactly when the next scheduled backup is largely on its own, based on the user's preferences about whether to backup once a day, once a week, etc. There is no way to currently specify "as close to 4AM on Thursday as possible". See bug 479191 for the related feature request.

**Why Not Cron?**
A monitoring program is used because access to the user session is useful for:
[LIST]
[*]prompting for passwords
[*]displaying status in the panel
[*]watching for events like plugging in a remote disk or becoming connected to the Internet
[/LIST]
One disadvantage is that a backup can not be started while a user is not logged in. The primary use case for Déjà Dup is backing up user data, so this is not a large concern, as user data is unlikely to change while the user are not logged in.

---

### Post by ken3 on 2013-08-01
That said, you could probably achieve something similar to a continuous backup if you have an external drive and set up RAID1.  You wouldn't get rollback, but you'd have a backup.

---

