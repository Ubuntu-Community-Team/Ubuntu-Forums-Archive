---
title: "Schedule btrfs scrub?"
date: 2016-03-10
forum: General Help
---

### Post by bug5 on 2016-03-10
What's the recommended way to do it?

Thanksin advance

---

### Post by TheFu on 2016-03-10
I scrub my mdadm arrays using a crontab entry every week.

---

### Post by david509 on 2016-06-29
How do you setup a scheduled cron to run btrfs scrub weekly?  What happens if the cron job is missed, will it run next time the computer is switched on?

---

### Post by TheFu on 2016-06-29
Don't know anything about btrfs, but cron can be setup to run at specific times or at "sometime" dependent on the period. @daily, @weekly, @monthly, @yearly, @hourly ... you get the idea.  For a system task like this, I'd setup a link in /etc/cron.weekly.  There should be examples in that directory. They are just scripts - basically the commands to be typed placed into a file. There are at least 3 different types of crontabs, so if you decided to use a different method, the format is different in each.

By default, mdadm scrubs monthly (which I learned later), but I decided that wasn't often enough.

I'd have to google or check the manpage for anything related to btrfs, so you can do that just as easily.  It doesn't appear to be anything special - just a command run as root which a weekly crontab setting will do automatically. [https://btrfs.wiki.kernel.org/index.php/Manpage/btrfs-scrub](https://btrfs.wiki.kernel.org/index.php/Manpage/btrfs-scrub) is the manpage. Something like **brtfs-scrub start /dev/sdXYZ** where sdXYZ is the path to the file system device.  Probably best to use /dev/disk/by-*/..... on a system with lots of disks.  Post the output from **lsblk** and **sudo blkid** if you need help determining stuff.

Hopefully someone else with btrfs experience will respond if anything said is incorrect above. I only know a few people running it on other distributions. Btrfs is an amazing file system, just a little new for my requirements.

---

### Post by david509 on 2016-07-06
It would be great if Ubuntu included a scrub cron job, weekly, when Btrfs (or ZFS) is used.  I believe both Btrfs and ZFS file systems require a "scrub" every week on desktop drives, to uncover any bit rot and possibly repair the damage?  End users will not remember to run a scrub every single week.

---

