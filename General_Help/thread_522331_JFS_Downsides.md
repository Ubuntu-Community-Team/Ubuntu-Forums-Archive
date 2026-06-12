---
title: "JFS Downsides?"
date: 2007-08-10
forum: General Help
---

### Post by Luke.Hoersten on 2007-08-10
I've just installed my new system on JFS and a friend mentioned that it will drop any open files if the drive is not unmounted properly (power outage, etc). I'm looking for documented downsides of JFS. Does anyone have any good articles for this?

Thanks.

---

### Post by stevecs on 2007-09-27
No good articles, but as I just posted elsewhere, any filesystem will have a much higher risk of problems if you drop power/unmount cleanly.    sysadmin rule #1, if it hurts don't do it.  :)      From doing a bunch of local testing on various FS's under linux I've found if you're <8TB EXT3 is probably the most reliable.   If you're >8TB than JFS is currently.  Perhaps in ~year or so EXT4 will be but since its still experimental let others find those problems for you.

---

### Post by articpenguin on 2008-01-30
hi
I have been using JFS for the last year. Its pretty fast. I have lost some speed though. well thats because my drive is always near full 90% most of the time. The speed i have lost is still more faster than ext3 is on my computer.

Downsides-
slow on deleting large amounts of files (over 10k)
JFS is only maintained by one guy who works on it part time
does get a little fragmented but still much less than ntfs or vfat

---

