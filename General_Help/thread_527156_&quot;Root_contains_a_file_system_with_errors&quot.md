---
title: "&quot;Root contains a file system with errors&quot;"
date: 2007-08-16
forum: General Help
---

### Post by Not So Smart Guy on 2007-08-16
So upon start up the system check starts and reports something to the tune of "Root contains a file system with errors... forcing check" than proceeds to report "0.6% uncontagious." The same process repeats itself with /home and reports "7.4% uncontagious" and then I boot up per usual. 

I looked around a bit and found others that have gotten a message warning of a file system with errors have also gotten a read out about "unexpected inconsistency" and to run fsck manually. Just to be clear I DO NOT get anything like, just the percentage and the uncontagious bit.  

Nothing seems out of place, and everything seems to be working perfectly so far. I just thought I'd post it here to see if anybody else has run into this, to find out if it's a serious problem, and what to do about it.

If anyone has any thoughts, that would be great. Thanks.

---

### Post by kidders on 2007-08-17
Hi there,

> **Not So Smart Guy said:**
> So upon start up the system check starts and reports something to the tune of "Root contains a file system with errors... forcing check" than proceeds to report "0.6% uncontagious."Heh... I think you mean non-contiguous.

If you're concerned about filesystem damage, you should run fsck yourself & see what happens. If you encounter errors, it's often a good idea to re-run the check, just to make sure everything was fixed properly. Ubuntu shouldn't do these checks unless it has a reason to.

---

