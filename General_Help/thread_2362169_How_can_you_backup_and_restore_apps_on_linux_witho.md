---
title: "How can you backup and restore apps on linux without internet?"
date: 2017-05-25
forum: General Help
---

### Post by ahawkua on 2017-05-25
I want to be able to backup my installed apps on linux and restore them on another computer with the same 64 bit linux OS without internet. how could i do this?

---

### Post by TheFu on 2017-05-25
There are a few different ways.
```
$ dpkg --get-selections > /tmp/list-o-pkgs
```
will make a list. How you move that list to a newly built, minimal box, is left as an exercise.
Then use 
```
$ dpkg --set-selections <  /tmp/list-o-pkgs
```
on the other machine. Then use **[dselect]("http://manpages.ubuntu.com/manpages/xenial/man1/dselect.1.html")** to install all of them.

You'll need to deal with providing the .deb files somehow. Creating an apt-cache might be a way. I dunno that part. Sorry.

There's another tool, I don't remember the name. apt-mark? Think you can request only manually installed packages with apt-mark. This should be better than using the full (get everything) dpkg --get-selections.  I've never used apt-mark, but use the dpkg method.

Or you could just mirror the OS install completely. Many different ways to do that. dd, ddrescue, partimage, clonezilla, fsarchive, or any of the more efficient backup/restore tools.

I had an OS and data holding disk failing last week. Purchased a new HDD of the same size and used ddrescue to mirror bit by bit from the old disk to the new disk.  This was 4TB of bits. Took over a day.  There were lots of errors because the old disk was failing. The errors were all outside the OS, just in the data areas, so a restore of the last data backup onto the new disk solved that issue. Part of the errors included a corrupted DB.  The restore from backup fixed that too. 

Of course, taking a look at the manpages for each command wouldn't hurt.

Hopefully someone else will provide a package caching solution you also need.

---

### Post by dragonfly41 on 2017-05-25
Might Aptik help?   It is a migration/backup utility (gui) in Ubuntu Software Centre.

---

