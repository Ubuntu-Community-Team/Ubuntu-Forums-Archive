---
title: "Quest: filesystem backup to blu-ray BD-R"
date: 2013-09-08
forum: General Help
---

### Post by Coder88 on 2013-09-08
So I am on a quest to find ways to back up my tweaked ubuntu/linux installation. Have a thread going elsewhere about using tar for this, that is going fine, doing a tar backup as I type this post actually. Can then backup my tarball to a networked data drive. But I came across this webpage explaining how to possibly backup to a blu-ray BD-R disc and I want to give it a try. If anybody else is interested, the game is afoot and I welcome collaborators to see if a filesystem can be backed up to blu-ray.
[http://www.troubleshooters.com/linux/blu-ray-backup.htm](http://www.troubleshooters.com/linux/blu-ray-backup.htm)
Involves some strange new linux commands, always a good thing to learn a few new commands. I have a blu ray burner and some 35GB BD-R data discs so what the heck, why not give it a try. My goal is to backup my installed linux system ("/") and all the files in it, excluding /proc, /home, and excluding any external filesystems mounted in / such as /Windows7

---

### Post by TheFu on 2013-09-08
**mkisofs** is the tool that I'd expect to be used for writing to optical media.  Found this: [http://fy.chalmers.se/~appro/linux/DVD+RW/](http://fy.chalmers.se/~appro/linux/DVD+RW/) seems that people are doing it already.  Don't know anything about this, since backups of an OS are so much easier to HDD. I'm still using DVDs for large data backups. I always add 10% par2 files so that a minor disc issue can be corrected and the data re-burned to newer DVD media.

I've read about all the people who seem to lose data on optical media.  Out of 500+ discs, only 3 have shown any issues with reading.  Some are from 2002 and still work fine.

**par2** and **ddrescue** can work wonders for discs that are not completely trashed. None of my discs has ever been that far gone to be completely unreadable before I move the data.  Though some minor data has been lost from the pre-par2 days.  I'm not using archive quality media either ... just the cheapo $20/100 and store them in a 300 disc holder in the closet.

For server and desktop backups, do not backup programs at all.  I backup data, home, settings, lists of packages. With just these, the system can be restored very quickly, provided your systems are consistently patched.  If you have an apt-cashe-ng server, even the updates will be local.  **dpkg --get-selections > ~/list-o-packages **is an amazing command.

---

