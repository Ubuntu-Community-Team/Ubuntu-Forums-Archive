---
title: "Automatically put hard drive to sleep?"
date: 2013-01-07
forum: General Help
---

### Post by Roasted on 2013-01-07
In my server I have two drives. Drive A is the one I work from and drive B is a backup, which gets rsync'd from A at midnight every night. I'm curious if there's a way to put drive B to sleep, preferably based on however long it's idle. Since it's a backup drive it'd be nice to put it to sleep after say 10 minutes of inactivity, then leave it hibernating all day until midnight when the rsync script calls for it again.

What would I need to accomplish this task?

---

### Post by CharlesA on 2013-01-07
Check out hdparm.

[http://blog.mymediasystem.net/uncategorized/simple-way-to-spindown-a-sata-hard-disk-drive-after-being-idle-linux/](http://blog.mymediasystem.net/uncategorized/simple-way-to-spindown-a-sata-hard-disk-drive-after-being-idle-linux/)

---

### Post by Roasted on 2013-01-08
Good find. Thanks for that! Am I under the correct understanding that as long as my BIOS supports AHCI that I can do this to SATA drives? Some of the discussion about SATA vs IDE got me a little confused on exactly what's supported and what isn't.

---

### Post by CharlesA on 2013-01-08
Not sure. As far as I know, AHCI, allows for some nice features, but I do not believe it does anything on the power management side of things.

I did find some more info on hdparm here:
[http://sobell.com/mgsblog/archives/5](http://sobell.com/mgsblog/archives/5)

Sounds handy, but I haven't used it much as I don't have my drives set to spin down when not in use.

---

### Post by Roasted on 2013-01-09
I hear ya. I don't have mine spinning down either on my other systems, but I also shut all of my computers off when I'm not using them with the exception of my server. If I can save a few bucks a year by inputting some sort of script that turns off my server's backup drive for 23.5 hours a day, I'm certainly game. :D

Thanks for the input!

---

### Post by Roasted on 2013-01-13
So I found out that I can put the HDDs to sleep by UUID with the -Y flag, i.e.:

hdparm -Y /dev/disk/by-uuid/f289e8ra98d9f8a9sd8f9asd

Only thing is, I added it to the very end of my rsync script. If I do this, the drive wakes itself back up about 15 seconds later. I'm a little unsure as to why...

---

