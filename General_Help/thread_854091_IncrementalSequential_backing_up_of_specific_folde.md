---
title: "Incremental/Sequential backing up of specific folders"
date: 2008-07-09
forum: General Help
---

### Post by Buzzdee on 2008-07-09
Hey, 

I don't know how many of you have heard of Apple's "Time Machine". It's a backup utility running in the background which constantly watches your entire HD/some folders and backs up any changes incrementally on an external hard disk. This way, you can roll back to any state a folder had in the last xx days.
Sounds great, doesn't it?

I wonder if there is anything alike for Linux - this would be a great thing for the next distro. I mean, everyone knows that it's important to regularly back up at least your ~ directory. But seriously... who does it? 

A programme like time machine needs more than a little disk space, but buying an external hard drive together with this programme would be more than worth the money. You don't have to actively back up and still have the highest possible safety - a past-raid system :D
Even if you don't get an external HD, a 10 GB partition should be more than enough to back up the really important data. 

Now, I just realised my post got a little away from the topic that I didn't find such a programme and more into the direction of animating some developers... :) 

What do you think, would it be worth-wile for you to program such a utility?

---

### Post by fjgaude on 2008-07-09
Well, with some skill all you have to do is learn **rsync** and **cron** and we have what Apple has.

Only those files that change need get re-written to the back-up partition or drive.

I use rsync, grsync, and **unison** for all kinds of back-ups, as needed.

Find someone to write you a script and its done, this back-up thing.

---

### Post by rraj.be on 2008-07-09
There is a  backup utility known as sbackup, it is very easy to setup. It does a full backup first and then only backups files that have been changed. You can set the interval on when it does a full backup and how often it just backs up changed files. Sbackup is in the repositories and you can use synaptic or Add/Remove Programs to install it.

```
sudo apt-get install sbackup
```

---

### Post by fjgaude on 2008-07-09
Yes, **sbackup** is another way to go. Thanks, rraj.be!

---

