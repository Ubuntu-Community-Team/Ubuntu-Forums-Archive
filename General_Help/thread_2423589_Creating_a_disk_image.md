---
title: "Creating a disk image"
date: 2019-07-25
forum: General Help
---

### Post by theimp2 on 2019-07-25
I'm trying to revive an old Dell Inspiron 1520 laptop that I managed to make completely FUBAR (more on that in another post).  
First things first, I want to backup everything so I don't end up screwing things up more than I already have.

I'd like to create an image of the hard disk such that I can restore it to the current state should things go awry (if only I had such foresight when I initially messed it up, sigh).

I'm using a live USB version of Ubuntu 18.04.2 LTS.

One thing I'll note is this disk has several partitions, including some that came directly from Dell (I don't have a recovery disk.. just the partition on the hard drive.. which I can't seem to access.. sigh.. but I'm getting ahead of myself again).

See the screenshot for what it looks like in the "disks" application.

How would I go about making an image of this?
I'm *guessing* I could do this:
```
dd if=/dev/sda | gzip -c > /path/to/usb/drive/backup.img.gz
```

But I'm not 100% sure of that and I'd like to verify I'm doing the right thing before executing a command that could potentially destroy all my data..

---

