---
title: "Raid mirror keeps failing but extended smart test OK"
date: 2013-11-11
forum: General Help
---

### Post by prioryjim on 2013-11-11
I have two 1T drives configured as a raid mirror
/dev/sdb1
/dev/sdc1
-----> /dev/md127

Worked OK for months.
However now when I copy vids to it the system fails sdc1 and runs degraded on sdb1.
dmesg shows some form of scsi parity error ( I could provide details ).
If I do a mkfs on /dev/sdc1 and then add it back into the mirror the system rebuilds the mirror (3 hours) and all is OK again.
Until I write to it again ?

The extended palimpsest check (take hours to run) says all is OK on sdc1.

Any ideas.
Thanks
Jim

---

### Post by CharlesA on 2013-11-11
Replace sdc and rebuild the array and try again. SMART checks aren't all they are cracked up to be.

---

### Post by prioryjim on 2013-11-11
Thanks
Would replace involve stress to my wallet ?
Jim

---

### Post by CharlesA on 2013-11-11
> **prioryjim said:**
> Thanks
Would replace involve stress to my wallet ?
Jim

Probably. At the very least, you should pull the failing drive out and run something like [this]("http://zackreed.me/articles/80-new-disk-stress-test") on it.

I've been using that to burn in new drives, but it should tell you if your drive is failing for sure or not.

But when in doubt, replace it. if it's still under warranty RMA it.

---

### Post by prioryjim on 2013-11-12
Thanks I will try the test.

Re warranty   ..
I had a single 1T WD drive with my vids on.
Last year it failed and I lost the lot, not really a problem as I can record stuff again.
However the drive was under warranty and WD sent a replacement.
The replacement only had a short warranty till Feb 2013.
I bought another 1T WD to make a mirror.
It has warranty till 2014 !

Guess which one is failing, yes the one out of warranty.
I wonder, are the WD replacement drive new ones or dodgy refurbished ones???

Anyway I won't be able to try the test till weekend.
Regards and thank for the effort, will update with result.
Jim

---

### Post by CharlesA on 2013-11-12
> **prioryjim said:**
> 
Guess which one is failing, yes the one out of warranty.
I wonder, are the WD replacement drive new ones or dodgy refurbished ones???

Probably refurbished. Sucks about the warranty. :(

---

### Post by prioryjim on 2013-11-25
Ran the .sh  script. It didn't seem to report any problems.
But there were some entries in 'dmesg' about write errors.
Bought a new drive £49 ish.
Fitted it yesterday and it look OK, it's now back in the mirror.
Will try copying to it again and see what happens.
Anyone want a cheap 1T drive ??
Thanks
Jim

---

