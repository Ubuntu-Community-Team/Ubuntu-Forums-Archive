---
title: "Reverting Video Driver"
date: 2006-11-18
forum: General Help
---

### Post by Augustus on 2006-11-18
I recently updated my video drivers from the one that came with edgy using the update manager (it said there was an update).  However, ever since the update, I have been unable to view my console.  I was wondering, does anyone know how to go back to the original driver, instead of updating?

(I have a ATI Radeon Xpress 200M, and it worked fine when I first installed edgy, that's why I want to downgrade...I just don't know how.)

Thanks.

---

### Post by RFScheer on 2006-11-18
Instead, I would try to solve the issue by looking at /var/log/Xorg.0.log and correcting whatever it says was wrong.  Post it here if you want.

If you really want to try and revert, you can look through the history in Synaptic (it's under File > History) and try and identify the new package that you think is responsible for the new problem.

If there are still old versions of that package in the repository, you can get rid of the new and force the old one.  But that's not how I'd proceed.

---

### Post by Augustus on 2006-11-18
[http://paste.ubuntu-nl.org/32546/](http://paste.ubuntu-nl.org/32546/)

I really don't know how to edit that...but I see there are problems.  Anyone have an idea of how to approach this next?

---

### Post by RFScheer on 2006-11-18
I'm not experienced with ATI cards but have you looked at 

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) ?

---

### Post by RFScheer on 2006-11-18
Oh, one more thing.  I'm wondering whether your screen was working orginally with the "vesa" driver and it stopped working when the proprietary driver was invoked?

I was expecting to see in your log file some reference to either "ati" or "radeon" drivers being loaded but didn't see either.  Like I said, I'm not experienced with ATI cards, but I thought there were 3 choices you could conceivably list in the xorg.conf file, ie "ati", "radeon" or "vesa".

Hopefully the guide will straighten it out for you.

---

### Post by RFScheer on 2006-11-18
Also this important thread.  Looks like you're not alone.

[http://www.ubuntuforums.org/showthread.php?t=290655](http://www.ubuntuforums.org/showthread.php?t=290655)

---

