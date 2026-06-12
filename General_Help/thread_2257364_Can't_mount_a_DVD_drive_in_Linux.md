---
title: "Can't mount a DVD drive in Linux?"
date: 2014-12-19
forum: General Help
---

### Post by harry28 on 2014-12-19
[FONT=arial][SIZE=2]I installed Linux Ubuntu on my Chromebook a month or so ago. I have recently started looking in Wine to install some Windows programs (specifically Office 2007). However when I plug my external DVD drive in (since it doesn't have an internal one), the dvd drive is not recognised. I plugged it once before and it was detected fine however for some reason now it isn't. I have tried many different things after searching on Google but nothing works. [This]("http://www.cyberciti.biz/faq/mounting-cdrom-in-linux/") was one of the pages that I looked at which got me a but further, however when i typed [COLOR=#111111]**lsblk** the dvd drive isn't shown. Is there any other way to mount the dvd drive?[/COLOR][/SIZE][/FONT]

---

### Post by llamabr on 2014-12-19
Plug the thing in, count ten missississis, and then post the last few lines of:

dmesg

---

### Post by harry28 on 2014-12-20
OK ran that and this a screenshot of the last few lines(couldn't copy and paste for some reason):
[IMG]http://i62.tinypic.com/2isw8r4.png[/IMG]

---

### Post by yancek on 2014-12-20
The output you posted shows the DVD drive is detected.  Do you not see anything under the /media directory when you put the DVD in the drive?  What is on the DVD?

You could try creating a mount point by opening a terminal and entering the following:  sudo mkdir /mnt/dvd
Then try mounting it:  sudo mount /dev/sr0 /mnt/dvd

That is a number zero in sr0, not a letter O.  Post back with the results.

---

### Post by mcduck on 2014-12-20
Seemes to be recognized just fine.

Keep in mind you can't mount optical media drive, only the actual media itself (hence the error about lsblk not finding anything, the drive itself isn't a block device...). Mounting is something you do with filesystems while empty drive doesn't have one.

---

### Post by harry28 on 2014-12-20
Tried doing that and it came up with the drive is already mounted. The disc which I was using is Office 2007 (installing it Wine) and I tried it on my Desktop before and it worked. However turns out it was nothing to do with the DVD drive and was to do with the DVD it self. When looking at (which I didn't notice before, not sure if the DVD drive has damaged it in someway) there is a considerable scratch right through the center of the disc which I can only assume means it won't be recognised. Sorry for being so stupid and not looking at this before but thanks for your help

---

