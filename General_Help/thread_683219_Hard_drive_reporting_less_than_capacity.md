---
title: "Hard drive reporting less than capacity"
date: 2008-01-30
forum: General Help
---

### Post by PinkFloyd102489 on 2008-01-30
Ive checked around some other threads to see if I could find my problem, but no such luck.

I have a 120GB secondary drive that only reports 111GB. Ive been trying to remedy this for sometime now, as I originally thought it may be slightly damaged. I run testdisk on it and it showed a lost partition, but now it doesnt. Is there any other way I can recover my 19GB of space?

---

### Post by Rocket2DMn on 2008-01-30
There is nothing to worry about, this is typical.  When they build drives, they are never truly what it says on the package because the measure a megabyte as 1 million bytes, when realistically it should be 2^10 bytes (which is cloes, but not quite 1 million).  Also, a little bit of space is used for firmware and whatnot.
Your drive is just where it should be.

---

### Post by logos34 on 2008-01-30
This causes so much confusion--there ought to be litigation against the hard drive manufacturers for misleading claims.  

Like rocket2dmn says, hard drive space is seen by the OS in [binary (base 2) ]("http://www.hardwaresecrets.com/printpage/482/1")form, where 1 GB = ~1,073,741,824 bytes, not decimal (base 10).  And then as soon as you format it ext3, 5% is by default reserved for root/admin. (you can lower the latter by using mke2fs with the appropriate options).

---

### Post by articpenguin on 2008-01-30
maybe he is using the ext3. Ext3 is a hog with space. On my 133GB partiton i lost 3GB thanks to the overhead of ext3.

changed to jfs and got my 3Gb back

---

### Post by logos34 on 2008-01-30
> **articpenguin said:**
> maybe he is using the ext3. Ext3 is a hog with space. On my 133GB partiton i lost 3GB thanks to the overhead of ext3.

changed to jfs and got my 3Gb back

just for future ref:  like I said above you can change the default 'reserved-blocks-percentage' ('**-m**' option)

e.g.:

sudo mke2fs -j **-m 1** /dev/<partition>  --> lowers it to 1%

or

sudo mkfs.ext3 -m 1 /dev/<partition>

---

### Post by articpenguin on 2008-01-30
thats what i did i originally lost 15GB did that tune2fs thing and regained 12GB but still lost 3GB. 
Besides JFS is a lot faster than ext3.

---

### Post by logos34 on 2008-01-30
hmm. 

I've been looking into XFS and JFS.  But aside from grub issues in XFS I may just stick with ext3 because it's proven so amazingly resilient through I don't know how many power outtages.  (I have no UPS on my linux workstation and ext3 journaling has saved my a** every time!).  Takes a licking and keeps on ticking...

---

### Post by Rocket2DMn on 2008-01-30
> **logos34 said:**
> hmm. 

I've been looking into XFS and JFS.  But aside from grub issues in XFS I may just stick with ext3 because it's proven so amazingly resilient through I don't know how many power outtages.  (I have no UPS on my linux workstation and ext3 journaling has saved my a** every time!).  Takes a licking and keeps on ticking...

While that is true, battery backups are the greatest invention since the terminal interface!  I got one on my server and one on my desktop, and they are lifesavers!

---

### Post by articpenguin on 2008-01-30
When my JFS lost power all it sayed was replaying journal log took 4 secs and my system was consistent. 

I did a stress test on ext3 and jfs. Unplugging my computer 30 times on each fs

ext3 said recovering journal most of the time and forced fsck 4 times
JFS just said the same thing every time replaying journal log.

---

