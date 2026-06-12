---
title: "How to completely destroy a Ext3 Partition"
date: 2008-05-27
forum: General Help
---

### Post by firemagican2845 on 2008-05-27
Hello,

I have a quick question for you all. We have a computer at work that will be shortly replaced. Since it contains data that should NEVER be accessed by others outside the company's HR department, how can we properly render the ext3 partition unrecoverable? It currently runs 7.04 Ubuntu. I know we can always do the sledge hammer to the hard drive trick but we'd like to avoid that if we can :) :lolflag: Any information would be helpful.


Thanks!

---

### Post by kesman on 2008-05-27
Short answer: you cannot, unless you physically destroy the drive. Even then, some information can be restored. There are companies that are experts at this and can even restore family photos from a hard drive that's been trough flame and firemen's water :P

---

### Post by firemagican2845 on 2008-05-27
> **kesman said:**
> Short answer: you cannot, unless you physically destroy the drive. Even then, some information can be restored. There are companies that are experts at this and can even restore family photos from a hard drive that's been trough flame and firemen's water :P

Thanks for the answer, I figured as much. Oh well the 500 hits of a sledge hammer till it's in tiny pieces will have to do! (I actually advocated for it, the powers that be however wanted to go the cheap way and not buy a hard drive to replace it!)

---

### Post by RAOF on 2008-05-27
Again, this depends on how sure you need to be.  If the data absolutely cannot be allowed to escape, melt the drive down.  **Guaraneed*** unrecoverable.

You probably don't need that degree of absolute certainty, however.  Booting from a live cd and running
```

sudo dd if=/dev/urandom of=/dev/*harddive_device*

```
a couple of times should be reasonably safe.  This will write random bits to the hard drive, and doing it a couple of times should make it fairly difficult to forensically extract the overwritten data.

* By some random dude on the internet, which is obviously the sort of guarantee you're after :)

---

