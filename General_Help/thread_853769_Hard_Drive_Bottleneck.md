---
title: "Hard Drive Bottleneck"
date: 2008-07-08
forum: General Help
---

### Post by Aikon- on 2008-07-08
Is there a way to tell which hard drive is the bottleneck when copying large files?

Sometimes when copying between hard drives I can get 30+ MB/s, others I only get 9.6MB/s. I would love to be able to isolate the problem drive, then either figure out what the problem is or buy a new drive.

-Aikon

---

### Post by iaculallad on 2008-07-08
Had you tried the badblocks utility? It can do both read and write test. But be careful on using this utility because it could kill your data.

```
man badblocks
```

---

### Post by bluepowder7 on 2008-07-08
are the files you are copying (the source files) possibly fragmented, like the results of a week-long torrent download?  i've seen a similar 3-to-1 ratio when i was moving files from my desktop's hard drive to my file server - some went at nearly the full 100Mbit (network) rate, others poked along at only 20 or 30 Mbits.  i can't recall if there was a performance figure in the system monitor or just my own massive brainpower, but i quickly sussed that the fragmentation of the source file was causing more seek times than actual transfer times.

---

