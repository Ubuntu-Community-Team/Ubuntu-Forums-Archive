---
title: "When is a hard drive unmounted?"
date: 2019-09-22
forum: General Help
---

### Post by delooper on 2019-09-22
Greetings, 

I've been an ubuntu user for more than a decade now.  One thing that has always confused me is determining when a drive is unmounted. 

Often I connect a USB drive to my system, run a backup that copies files to the external USB drive, then I hit "unmount".   My current version of Ubuntu (18.04) puts a little dialogue at the top of one of my screens that suggests to wait before unplugging the drive.  

But wait until when? 

In practice, I wait until I can no longer hear the drive heads moving.  But if I had an external SSD drive, I wouldn't be able to hear the activity.  

How do you know when the drive is done with the unmount process, i.e. done flushing the cache?

---

### Post by Skaperen on 2019-09-22
it's hard to tell but if you were in command line mode there is an easy way.  the amount of time is usually quick, but if you did a a lot of writing and have a lot of RAM, it could take a while.  with my 16 GB RAM i've seen over a minute, once.  i time big commands and have ";time sync;time sync" after it.

---

### Post by HermanAB on 2019-09-22
The mount -I command will tell you what is mounted.

[https://linux.die.net/man/8/mount](https://linux.die.net/man/8/mount)

---

