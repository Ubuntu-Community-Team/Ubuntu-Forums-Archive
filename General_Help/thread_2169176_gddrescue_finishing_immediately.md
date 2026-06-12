---
title: "gddrescue finishing immediately"
date: 2013-08-20
forum: General Help
---

### Post by TurkVU on 2013-08-20
Trying to recover data from a raid array that was in a DLink-323 as it started to fail following the accidental deletion of a folder with a ton of files in it. I immediately started copying as much data as I could off the drive, got most, now I'd like to create a drive image so I can try to recover the accidentally deleted data. Hoping that gddrescue could help with image creation.

I removed the drives from the NAS and put them in my PC, then mounted the array read-only (/media/raiddisk)

I then mounted a NAS that I'd like to create the image on (/media/Data)

Then I ran:

```
sudo ddrescue -n /media/raiddisk /media/Data/image.img /media/Data/logfile
```

The routine finished immediately with this: 

```
Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:    4096 B,  errors:       1
Current status
rescued:         0 B,  errsize:    4096 B,  current rate:        0 B/s
   ipos:         0 B,   errors:       1,    average rate:        0 B/s
   opos:         0 B,     time from last successful read:       0 s
Finished

```

Wondering if the block size is throwing ddrescue or if there's something in my syntax that's off...

Any help would be appreciated.

---

### Post by TurkVU on 2013-08-21
Figured this one out - I had to unmount the raid array. I kept it started, but unmounted.

---

