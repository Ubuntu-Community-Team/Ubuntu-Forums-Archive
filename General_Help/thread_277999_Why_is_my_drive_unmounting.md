---
title: "Why is my drive unmounting?"
date: 2006-10-15
forum: General Help
---

### Post by driggins on 2006-10-15
Greetings,

Linux newbie here.

I have installed a second hard drive, setup as slave on the second IDE channel. Ubuntu sees it as "hdd".

I setup a cron job last night to rsync data from the hd1 partition to a removeable USB drive. This morning, I found that hd1 was unmounted. I was able to mount it again without a problem.

My question is this: why might hd1 have unmounted? What can I do so that it does not do so in the future?

Since I share hd1, I need to make sure it is always available.

In the case that the rsync job is pertinent, here's the command I used in my cron job:
```
rsync -av /media/data/Shared /media/backup/Shared
```

Thanks for your input!
daryl

---

