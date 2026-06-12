---
title: "Where is the disk mount tool in Feisty?"
date: 2007-02-18
forum: General Help
---

### Post by ahood on 2007-02-18
Hi All,

I am using Feisty Herd 4 and there is a new Control Panel; however, I don't see the disk mount utility that is in Dapper. This was a handy utility for mounting Windows partitions (ready-only is all I need). I can do this manually, but the disk mount utility was good for newbies (at least I thought so). 

If this disk utility is somewhere and I am not seeing it, please point me in the right direction.

With kind regards,

Al Hood

---

### Post by moshuptrail on 2007-02-18
I heard they left it out in Edgy.  So the somewhat glib answer is, in the command line.  Sorry.
Maybe someone else knows an equivalent.
(I never heard why, although the few times I used it gave me problems when remounting)

---

### Post by ahood on 2007-02-18
Thanks! 

I didn't update to Edgy (hehe).

Although I didn't have a problem with it, if it was unstable or problematic...may be best to leave it out until another time...

Al

---

### Post by fragos on 2007-02-18
There's a package in Edgy Synaptic called "psydm" that with add an administration icon for "Storage Package Manager."  This is different than what's in Dapper but has done the job for me.  There's a chance you'll find it in Feisty of do a synaptic search for "storage device manager."

---

### Post by ahood on 2007-02-19
Thanks Frago!

Will give that package a try. definitely. 

When I entered the command to mount my windows partition (NTFS), I discovered that Feisty already mounted it to /media/hda1, which is very nice. I don't recall Dapper, or previous versions of Ubuntu, auto mounting the Windows partition.

Thanks everyone for the help!

Al

---

