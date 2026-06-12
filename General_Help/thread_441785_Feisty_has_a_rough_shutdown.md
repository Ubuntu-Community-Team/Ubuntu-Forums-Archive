---
title: "Feisty has a rough shutdown"
date: 2007-05-12
forum: General Help
---

### Post by zcal on 2007-05-12
I recently installed Feisty (was using Edgy previously).  This problem did not occur in Edgy, Dapper, nor Breezy.

In previous versions of Ubuntu (and Windows XP), everything went smoothly when shutting down.  But in Feisty, it doesn't seem to be stopping the hard drive before cutting the power.  The drive emits a sort of "bark" when the power turns off, which I can only assume comes from not being shut down previously.  I'll get the same type of noise if I pull the power cord out of the laptop and don't shut it down within a few minutes (I need a new battery) because the laptop will abruptly turn off rather than getting enough time to shut itself down before it drains the last of the power.  Obviously, this rough shut down is something that shouldn't be happening (I hope!).  Anybody know anything about this issue? :confused:

---

### Post by ronacc on 2007-05-12
I have 3 feisty installs and none of them exhibit this behavior although also none of them are on laptops.Feisty does boot and shutdown quickly , perhaps yo could add a few seconds wait late in the shutdown script.

---

### Post by zcal on 2007-05-13
How would I get into the shutdown script to mess with it?  Would a "halt" action do the trick?

Could an admin maybe move this to the hardware subforum?  I think it might be more appropriate in there...

*edit*
I forgot, I also just did a fresh reinstall of Feisty, just to see if it would fix anything.  Nope.  Still with the rough shutdown.

*edit 2*
*sudo halt -h* which, as I understand, ought to power down the hard drive before shutting down does not solve this problem either.  I think ronacc is right in that it's just cutting the power too quickly.  How can I add a few seconds wait to shutdown?

*edit 3*
I changed the 'sleep' timer in the S90halt script (/etc/rc0.d) to wait 5 seconds instead of 1 before using 'halt' to power the system down.  Still no change.  I'm wondering if I might need to set a 'sleep' timer in a different place within the script...

Otherwise, I'm thinking either the script isn't shutting down the hard drive because it thinks that I'm using RAID (the fact that *sudo halt -h* didn't change anything doesn't seem to support this theory), or this is a kernel bug.  Either way, I'd like to get this problem solved.  I'm worried about my hardware.

Does anyone else experience this problem?

---

### Post by zcal on 2007-05-14
bump

---

### Post by kaar3l on 2007-05-17
I have exacty the same problem, but with kubuntu.

---

### Post by zcal on 2007-05-17
> **kaar3l said:**
> I have exacty the same problem, but with kubuntu.

It's a kernel bug.  Check out [this thread]("http://ubuntuforums.org/showthread.php?t=437599").  I've posted links there to more information and how to fix it until the kernel gets patched.

---

