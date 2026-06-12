---
title: "Best way to check a new hard disk for bad sectors and other defects/malfunctions"
date: 2013-03-01
forum: General Help
---

### Post by SaturnusDJ on 2013-03-01
I need to test 3x 2TB hard disks before putting them to use.

I'll use smartmontools to do long S.M.A.R.T. tests. Also I want to verify all of the space:

Three choices:
**1. dd**. Standard block size is 512 bytes. 
**2. ddrescue**. I've read that this commands does not give up that easily as dd does when receiving errors, and follows a different style. (See quote bellow.) Standard block size is 512 bytes. With 128 at the same time. ([Source]("http://ss64.com/bash/ddrescue.html"))
**3. badblocks**. Standard block size is 1024 bytes. With 64 at the same times. ([Source]("http://linux.die.net/man/8/badblocks"))


After reading this about **ddrescue **I got a little worried:
[quote=http://ubuntu-rescue-remix.org/node/51]It notes in the logfile that a bunch of sectors (the first erroneous one, plus whatever ones followed it in the multi-sector read) were skipped. And keeps going. So it reads through the entire disk in big blocks first. Then it goes back to "split" the skipped parts, trying to read each sector individually.[/quote]
My goal is to verify the health of **every bit** on the drives, read and write. Will this be accomplished when using ddrescue?
**What is the best way to test these drives?**

[SIZE=1]NB. Fixing errors is not necessary. If any are to be found, I'll DOA the disk(s).[/SIZE]

---

### Post by SaturnusDJ on 2013-03-02
Kick.
Please reply someone.

---

### Post by schragge on 2013-03-02
Neither *dd* nor *ddrescue* are designed to check the disk for defects. While *ddrescue* tries hard to salvage your data from bad blocks, it will not mark unreadable blocks as bad. Besides, you should use these commands at least twice, first reading from the disk, then writing to it if you want to catch both read and write errors. And even then, they don't write some pattern, then check if that pattern was written correctly like what *badblocks -w* does.

On an unformatted device, try
```
badblocks -v -w

```

---

### Post by SaturnusDJ on 2013-03-02
That about the pattern verification by badblocks is a very good point! Choice is made. Thank you.

---

