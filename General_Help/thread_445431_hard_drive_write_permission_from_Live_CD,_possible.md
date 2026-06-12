---
title: "hard drive write permission from Live CD, possible?"
date: 2007-05-15
forum: General Help
---

### Post by Junction on 2007-05-15
My apologies if this is a stupid question, but I was wondering if it is possible for me to boot from a Live CD, and from there be able to write to a partition that already has Ubuntu installed on it.

Basically, when I upgraded from Edgy to Feisty, I went from having the rare but occasional lockup where I could still move the mouse and use the keyboard, to very frequent lockups where even the mouse and keyboard become unresponsive.  It is quite possible that I just screwed something up at some point, so I figured I'd see if using a Live CD would have the same trouble, and so far I've gone about half an hour without a lockup, which is the longest Ubuntu experience I've had since I upgraded to Feisty.  I'd like to see how the Live CD handles things over a few more days, but would also like to be able to save stuff to a hard drive while I'm still on the Live CD.  Is this possible?

---

### Post by BeardlessForeigner on 2007-05-16
Although I'm new to linux, I installed off the ubuntu live cd and used it to copy my ibm hidden partition to a flash drive. You should be able to mount and read from other drives and write to them as long as they are something like ext3 and fat32.

---

### Post by Junction on 2007-05-16
Cool.  I did a google search to find out a bit more about mounting and such, and following the instructions from [here](http://www.psychocats.net/ubuntu/mountlinux), I was able to mount my linux hard drive while booted to the live CD.  Yay!

Unfortunately, the Feisty CD turned out to be no stabler for me than my installation, but I found out how to do what I was wanting to do, so that'll help me in the future.

Edit:  Hmm, it seems that doing this sorta screws up with logging in when booting from that hard drive.  Oh well, will probably end up reinstalling at some point anyway.

---

