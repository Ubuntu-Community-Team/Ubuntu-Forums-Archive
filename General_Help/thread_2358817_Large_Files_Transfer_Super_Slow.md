---
title: "Large Files Transfer Super Slow?"
date: 2017-04-17
forum: General Help
---

### Post by taylrox on 2017-04-17
Hi all,

I'm copying over 100Gb of data from my laptop to my external HDD (Around 10Gb a file) and I noticed that for the first 10 minutes or so the copy was going at a good 20-25MB/Sec and giving me an estimated copy time of just under an hour. So I've buggered off and watched a bit of TV for an hour whilst I kill the time for things to back up but upon returning to the laptop it has slowed down dramatically to around 1-2MB/second and is now displaying a copy time of 20+ hours? Anyone else experienced this and had this problem/found a solution?

The external HDD is a 1TB Western Digital USB 2 drive and the laptop is your bog standard 300Gb HDD (laptops HDD format is EXT4 and the external HDD format is FAT32). 

I'm just confused as to why it was flying on the first and second file but then slowed down MASSIVELY when progressing? It's not even fluctuating between fast and slow, it's just dramatically slowed down and maintaining the slower speed. I have all sleep features and what not disabled so the laptop hasn't gone into standby or anything.

I'm copying via the good old standard copy and paste from one folder to another (via GUI).

Any help would be greatly appreciated.

Regards,

Tayl.

---

### Post by TheFu on 2017-04-17
Are all devices plugged into power?
For stuff like this, I'd use rsync for a number of reasons.  Mainly because if something fails (USB2 connection problem), then rerunning the same rsync won't copy already copied data again.

---

### Post by taylrox on 2017-04-18
Hi TheFu,

Yes, both the laptop is running via the mains adapter and also the external HDD has it's own power supply.  

How do you use rsync? I've tried looking it up but not found something clear enough to understand. And does it matter that I already have data on the HDD and wish to add new files to it?

---

### Post by TheFu on 2017-04-18
rsync manpage says:
```
rsync(1)                                                              rsync(1)

NAME
       rsync - a fast, versatile, remote (and local) file-copying tool

SYNOPSIS
       Local:  rsync [OPTION...] SRC... [DEST]
```

The manpage has lots of good example with explanations, so I won't repeat them here.

So .... 

```
$ rsync [options] source destination
```
would be the typical normal usage.  Try it out on something small. See how it works. Nothing will replace trying it out. Run the same command a few times - what happens? The "source" isn't modified, unless you make the destination somewhere that is also part of the "source" area. That would be bad.  There are thousands of webpages about using rsync and hundreds of youtube videos about it.

If I want to make a copy of my /etc/ directory, without the root-only files, then I'd use 
```
mkdir ~/temporary-area/
rsync -avz /etc  ~/temporary-area/
```

Play around with small test areas. See what happens.  There's a test-only mode with rsync too.

---

