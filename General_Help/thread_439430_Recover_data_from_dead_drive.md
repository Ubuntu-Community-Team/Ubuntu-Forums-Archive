---
title: "Recover data from dead drive"
date: 2007-05-10
forum: General Help
---

### Post by saracen on 2007-05-10
I think I just lost one of my drives to oblivion.  It just gives off a continual clicking noise when it's plugged in and my PC doesn't boot at all.  When I unplug the drive I can boot in (my root partition is on another drive).  But that dead drive was part of an LVM that had 3 other drives under it as well.  So I have 2 questions:

1) Can I recover the data on the dead (clicking) drive?
2) The data on the other drives should be intact, but I have no idea how to recover the data from them or re-adjust the LVM with just the remaining 3 drives.  What should I do?

It's terrible when this happens... I hope that someone out there can help  :(

---

### Post by Yoooder on 2007-05-10
That's bad :( 

I'm not sure, but my impression/understanding is that LVM doesn't provide any form of redundancy.  I've always relied on RAID on top of LVM for recovery needs.

---

### Post by saracen on 2007-05-10
Yeah... I know there's no redundancy but the data is still on the good drives so there must be a way to recover at least the data on the good drives.  I'm not sure about the dead drive but if anyone has ideas for that one too i'd really appreciate it.

---

### Post by Xeor on 2007-05-10
You can hope that it's the circuit board who went bust. If that is the case, you can try to find the same hard drive and just change the circuit board to make it work long enough to retrieve the data.

---

### Post by saracen on 2007-05-11
Yeah, i'm going to take the dead drive somewhere to see if i can recover anything from it.  How about the rest of the drives that are still good and were part of the LVM?  How do I get the LVM setup back and have it see the data that's on those drives?

---

### Post by saracen on 2007-05-12
Is anyone out there an LVM expert?

---

