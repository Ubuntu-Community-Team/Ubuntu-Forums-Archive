---
title: "truecrypt 5.0a woes"
date: 2008-02-28
forum: General Help
---

### Post by mindunit on 2008-02-28
having:
1) installed truecrypt 5.0a
2) created a truecrypt volume on an external 500g hdd (with reiserfs inside)
3) upgraded to my ubuntu kernel to 2.6.24-10 (as recommended)
4) mounted it in the GUI with options of 'sync' (-m or --mount-options doesnt work on commandline!)

writing no longer hangs, but my write speed (with or without 'sync') is no more than 0.5 mps... which is unacceptable on a 300gig per day backup scheme. (it would take 5 days to complete...)

the server and USB2 should be capable of at least 20 or 30 times that, even with encryption... (i'd even be happy with the 11mps some people have been reporting)

i'm really at a loss to explain whats going on here - and if no one has any other suggestions, i'm going to be forced to revert LUCS.
any ideas?

---

### Post by anitract on 2008-02-28
You might want to give 4.3a a try...a lot of us are still using that version as it seems that v5 was a step backwards in so many ways.  I don't believe that the container you made w/ 5.0a will be backward compatible though (I could be wrong here)...

---

### Post by wieman01 on 2008-03-02
Same problem here... write speed is awfully slow (0.5 - 1 MB/sec). Oh well... nothing is perfect.

---

### Post by wubrgamer on 2008-03-03
WHY did they remove the command line capabilities ?


That is such bull...is there any plan to re-implement them ?

---

### Post by chewearn on 2008-05-04
Sorry to resurrect and old thread.  Anyone got Truecrypt 5.1a working in Hardy?

I just installed it on Hardy, but the write speed to stuttering from 0 to 1 MB/s.  Is there a solution?

---

### Post by wieman01 on 2008-05-04
There used to be a Sticky in the Truecrypt forum concerning this bug (bad performance). You could start there...

---

### Post by chewearn on 2008-05-04
There is a sticky there in truecrypt forum says you need to run the latest version kernel (no version mentioned).

Hardy is running 2.6.24, while the latest stable in kernel.org is 2.6.25.  I'm not sure if the sticky is a correct statement there.

Well, thanks for the help.  Looks like I might have to compile truecrypt 4.3a for Hardy.

EDIT:
Yay!  After an hour of google-fu and head scratching, success!  Followed this thread:
[http://ubuntuforums.org/showthread.php?t=647339](http://ubuntuforums.org/showthread.php?t=647339)

I only wish I knew how to build a deb file out of this.

---

### Post by skywalkin1138 on 2008-05-15
I'm running TrueCrypt 5.1a in Hardy writing to both ext3 and ntfs TC volumes.  Have had issues though.  Throughput is about 6-7 MB/s, but when moving large amounts of data the system hangs.

Tried updating version of ntfs-3g to 1.2506 in the hopes it was only the ntfs partition that was causing it, but also happens when writing to the ext3.  Was trying to run a VMware guest from it.  I may have to go back to TrueCrypt 4.3a and see if the issues still remanin.

---

